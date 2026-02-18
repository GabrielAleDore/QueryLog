# Planos de acesso

### **Remover EXPLAIN TABLES invalidas**
```Bash
db2 "call sysproc.sysinstallobjects('EXPLAIN','D',NULL,'DBA')"
```

### **Criar**
```Bash
db2 "call sysproc.sysinstallobjects('EXPLAIN','C',NULL,'DBA')"
```