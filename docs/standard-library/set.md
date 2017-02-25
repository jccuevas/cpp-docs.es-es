---
title: "&lt;set&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.<set>"
  - "std::<set>"
  - "<set>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "set (encabezado)"
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# &lt;set&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define las clases de plantilla de contenedor set y multiset, así como sus plantillas auxiliares.  
  
## Sintaxis  
  
```  
  
#include <set>  
  
```  
  
## Miembros  
  
### Operadores  
  
|Versión set|Versión multiset|Descripción|  
|-----------------|----------------------|-----------------|  
|[operator\!\= \(set\)](../Topic/operator!=%20\(set\).md)|[operator\!\= \(multiset\)](../Topic/operator!=%20\(multiset\).md)|Comprueba si el objeto set o multiset a la izquierda del operador no es igual que el objeto set o multiset situado a la derecha del operador.|  
|[operator\< \(set\)](../Topic/operator%3C%20\(set\).md)|[operator\< \(multiset\)](../Topic/operator%3C%20\(multiset\).md)|Comprueba si el objeto set o multiset a la izquierda del operador es menor que el objeto set o multiset situado a la derecha del operador.|  
|[operator\<\= \(set\)](../Topic/operator%3C=%20\(set\).md)|[operator\<\= \(multiset\)](../Topic/operator%3C=%20\(multiset\).md)|Comprueba si el objeto set o multiset a la izquierda del operador es menor o igual que el objeto set o multiset situado a la derecha del operador.|  
|[operator\=\= \(set\)](../Topic/operator==%20\(set\).md)|[operator\=\= \(multiset\)](../Topic/operator==%20\(multiset\).md)|Comprueba si el objeto set o multiset a la izquierda del operador es igual que el objeto set o multiset situado a la derecha del operador.|  
|[operator\> \(set\)](../Topic/operator%3E%20\(set\).md)|[operator\> \(multiset\)](../Topic/operator%3E%20\(multiset\).md)|Comprueba si el objeto set o multiset a la izquierda del operador es mayor que el objeto set o multiset situado a la derecha del operador.|  
|[operator\>\= \(set\)](../Topic/operator%3E=%20\(set\).md)|[operator\>\= \(multiset\)](../Topic/operator%3E=%20\(multiset\).md)|Comprueba si el objeto set o multiset a la izquierda del operador es mayor o igual que el objeto set o multiset situado a la derecha del operador.|  
  
### Funciones de plantilla especializadas  
  
|Versión set|Versión multiset|Descripción|  
|-----------------|----------------------|-----------------|  
|[swap \(set\)](../Topic/swap%20\(set\).md)|[swap \(multiset\)](../Topic/swap%20\(multiset\).md)|Intercambia los elementos de dos sets o multisets.|  
  
### Clases  
  
|||  
|-|-|  
|[set \(Clase\)](../standard-library/set-class.md)|Se usa para el almacenamiento y la recuperación de datos de una colección en la que los valores de los elementos contenidos son únicos y sirven como valores de clave según los cuales se ordenan automáticamente los datos.|  
|[multiset \(Clase\)](../standard-library/multiset-class.md)|Se usa para el almacenamiento y la recuperación de datos de una colección en la que los valores de los elementos contenidos no tienen que ser únicos y en la que sirven como valores de clave según los cuales se ordenan automáticamente los datos.|  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)