---
title: "Understanding Backus Nauer Form (BNF) Syntax | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Backus Nauer Form (BNF) syntax"
  - "BNF notation"
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Understanding Backus Nauer Form (BNF) Syntax
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los scripts utilizados por el registro ATL se describen en este tema mediante la sintaxis de BNF, que utiliza la notación mostrada en la tabla siguiente.  
  
|convención\/símbolo|Significado|  
|-------------------------|-----------------|  
|`::=`|Equivalente|  
|`&#124;`|OR|  
|`X+`|una o más s de `X`.|  
|`[X]`|`X` es opcional.  Los delimitadores opcionales denotados por `[]`.|  
|cualquier texto en negrita|un literal de cadena.|  
|Cualquier texto *pone en cursiva*|cómo construir el literal de cadena.|  
  
 Como se indica en la tabla anterior, los scripts de registro utilizan literales de cadena.  estos valores son el texto real que debe aparecer en el script.  La tabla siguiente describe los literales de cadena utilizados en un script de registro ATL.  
  
|literal de cadena|Acción|  
|-----------------------|------------|  
|**ForceRemove**|Quitar completamente la siguiente clave \(si existe\) y vuelva a crearlos.|  
|**NoRemove**|No quita la siguiente clave durante Anular.|  
|**val**|especifica que `<Key Name>` es realmente un valor denominado.|  
|**Eliminar**|Elimina la clave siguiente durante el registro.|  
|**s**|Especifica que el siguiente valor es una cadena \(**REG\_SZ**\).|  
|**d**|especifica que el valor siguiente es **dword** \(**REG\_DWORD**\).|  
|**m**|especifica que el valor siguiente es el multistring \(**REG\_MULTI\_SZ**\).|  
|**b**|especifica que el valor siguiente es un valor binario \(**REG\_BINARY**\).|  
  
## Ejemplos de sintaxis de BNF  
 A continuación se muestran algunos ejemplos de la sintaxis para ayudarle a entender cómo la notación y literales de cadena funcionan en un script de registro ATL.  
  
### Ejemplo 1 de sintaxis  
  
```  
<registry expression> ::= <Add Key>  
```  
  
 especifica que `registry expression` es equivalente a `Add Key`.  
  
### Ejemplo 2 de sintaxis  
  
```  
<registry expression> ::= <Add Key> | <Delete Key>  
```  
  
 especifica que `registry expression` es equivalente a `Add Key` o a `Delete Key`.  
  
### Ejemplo 3 de sintaxis  
  
```  
<Key Name> ::= '<AlphaNumeric>+'  
```  
  
 especifica que `Key Name` equivale a uno o más `AlphaNumerics`.  
  
### Ejemplo 4 de sintaxis  
  
```  
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name>  
```  
  
 especifica que `Add Key` es equivalente a `Key Name`, y que los literales de cadena, `ForceRemove`, `NoRemove`, y `val`, son opcionales.  
  
### Ejemplo 5 de sintaxis  
  
```  
<AlphaNumeric> ::= any character not NULL, that is, ASCII 0  
```  
  
 especifica que `AlphaNumeric` equivale a cualquier carácter no null.  
  
### Ejemplo 6 de sintaxis  
  
```  
val 'testmulti' = m 'String 1\0String 2\0'  
```  
  
 especifica que el nombre de clave `testmulti` es un valor multistring compuesto por `String 1` y `String 2`.  
  
### Ejemplo 7 de sintaxis  
  
```  
val 'testhex' = d '&H55'  
```  
  
 especifica que el nombre de clave `testhex` es un valor de **dword** establecido hexadecimal 55 \(decimal 85\).  Observe este formato se adhieren **a la notación** de &H como se encuentra en la especificación de Visual Basic.  
  
## Vea también  
 [Creating Registrar Scripts](../atl/creating-registrar-scripts.md)