# **Tree view**

!!! note "Como transformar o arquivo .rex de  Tree View  para Free Form"

### 1. Altera este trecho do código fonte:
```
processing=8 para processing=0
```

### 2. busca no fonte a seguinte chave:
```

export.xhtml()
```

### 3. abaixo remove a seguinte linha: 
```
tree(type=1 showconnectlines=yes showleafnodeconnectLines=yes indent=80 showtreenodeicon=no defaultexpandtolevel=1 stateiconalignmode=1  selectnodebymouse=no rtollayout=no) 
``` 

