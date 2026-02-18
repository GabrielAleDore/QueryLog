# **Código de Barras**

Sobre o código de barras de caixa com 14 ou 13 caracteres (ou código de barras que tem 13 caractere mas não lê na EAN-13).
Criei essa function no banco, queria pedir para o @Roberto Kozan - CISS e @Izomar Brugnera verificar para a fábrica conseguir colocar nas versões do banco:

```SQL
CREATE OR REPLACE FUNCTION UF_GENERATE_CODE128B_FLEX(ID_BARRA VARCHAR(50))
RETURNS VARCHAR(100)
LANGUAGE SQL
DETERMINISTIC
NO EXTERNAL ACTION
BEGIN
    DECLARE i INT DEFAULT 1;
    DECLARE checksum INT DEFAULT 104; -- Valor inicial fixo para START B
    DECLARE position INT DEFAULT 1;
    DECLARE current_char_val INT;
    DECLARE encoded_string VARCHAR(100) DEFAULT '';
    DECLARE start_char CHAR(1);
    DECLARE stop_char CHAR(1);
    DECLARE check_char CHAR(1);
    DECLARE input_len INT;

    -- 1. Caracteres de controle para a fonte (Mapeamento padrão Windows/ANSI)
    -- Start B = 204, Stop = 206
    SET start_char = CHR(204);
    SET stop_char = CHR(206);
    SET input_len = LENGTH(ID_BARRA);

    -- 2. Loop caractere a caractere (Modo B)
    WHILE (i <= input_len) DO
        -- Pega o valor numérico do caractere (ASCII - 32)
        -- Ex: '0' é ASCII 48. 48 - 32 = 16.
        SET current_char_val = ASCII(SUBSTR(ID_BARRA, i, 1)) - 32;

        -- Cálculo do Checksum: Checksum + (Valor do Caractere * Posição)
        SET checksum = checksum + (current_char_val * position);
        SET position = position + 1;

        -- Monta a string de dados
        SET encoded_string = encoded_string || SUBSTR(ID_BARRA, i, 1);
        SET i = i + 1;
    END WHILE;

    -- 3. Calcular Caractere de Verificação (Modulo 103)
    SET checksum = MOD(checksum, 103);

    -- Mapeia o checksum de volta para um caractere visível pela fonte
    IF (checksum < 95) THEN
        SET check_char = CHR(checksum + 32);
    ELSE
        SET check_char = CHR(checksum + 100);
    END IF;

    -- 4. Retorno final
    RETURN start_char || encoded_string || check_char || stop_char;
END
```