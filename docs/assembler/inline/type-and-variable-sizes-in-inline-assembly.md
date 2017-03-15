---
title: "Tama&#241;os de tipo y variable en los ensamblados alineados | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "length"
  - "Type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ensamblado en línea, operadores"
  - "LENGTH (operador)"
  - "tamaño"
  - "SIZE (operador)"
  - "tamaño, obtener en ensamblado alineado"
  - "TYPE (operador)"
  - "variables, longitud"
  - "variables, tamaño"
  - "variables, tipo"
ms.assetid: b62c2f2b-a7ad-4145-bae4-d890db86d348
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Tama&#241;os de tipo y variable en los ensamblados alineados
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Los operadores **LENGTH**, **SIZE** y **TYPE** tienen un significado limitado en el ensamblado alineado.  No se pueden utilizar en absoluto con el operador `DUP` \(porque no se puede definir datos con las directivas o los operadores de MASM\).  No obstante, puede utilizarlos para buscar el tamaño de variables o tipos de C o C\+\+:  
  
-   El operador **LENGTH** puede devolver el número de elementos de una matriz.  Devuelve el valor 1 para las variables que no son de matriz.  
  
-   El operador **SIZE** puede devolver el tamaño de una variable de C o C\+\+.  El tamaño de una variable es el producto de **LENGTH** y **TYPE**.  
  
-   El operador **TYPE** puede devolver el tamaño de un tipo o variable de C o C\+\+.  Si la variable es una matriz, **TYPE** devuelve el tamaño de un único elemento de la matriz.  
  
 Por ejemplo, si el programa tiene una matriz de `int` de 8 elementos,  
  
```  
int arr[8];  
```  
  
 las siguientes expresiones de C y ensamblado producen el tamaño de `arr` y sus elementos.  
  
|\_\_asm|C|Tamaño|  
|-------------|-------|------------|  
|**LENGTH** arr|`sizeof`\(arr\)\/`sizeof`\(arr\[0\]\)|8|  
|**SIZE** arr|`sizeof`\(arr\)|32|  
|**TYPE** arr|`sizeof`\(arr\[0\]\)|4|  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Usar lenguaje de ensamblado en bloques \_\_asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)