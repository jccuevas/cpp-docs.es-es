---
title: "&lt; map &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::<map>"
  - "std.<map>"
  - "<map>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "map (encabezado)"
ms.assetid: bbf76680-7362-456e-88fa-ecda93561b6a
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# &lt; map &gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define la asignación y la asignación múltiple de clases de plantilla de contenedor, así como sus plantillas auxiliares.  
  
## Sintaxis  
  
```  
  
#include <map>  
  
```  
  
## Miembros  
  
### Operadores  
  
|Versión de asignación|Versión de asignación múltiple|Descripción|  
|---------------------------|------------------------------------|-----------------|  
|[operator\!\= \(map\)](../Topic/operator!=%20\(map\).md)|[operator\!\= \(multimap\)](../Topic/operator!=%20\(multimap\).md)|Comprueba si el objeto de asignación o asignación múltiple del lado izquierdo del operador no es igual que el objeto de asignación o asignación múltiple del lado derecho.|  
|[operator\< \(map\)](../Topic/operator==%20\(map\).md)|[operator\< \(multimap\)](../Topic/operator==%20\(multimap\).md)|Comprueba si el objeto de asignación o asignación múltiple del lado izquierdo del operador es menor que el objeto de asignación o asignación múltiple del lado derecho.|  
|[operator\<\= \(map\)](../Topic/operator%3C%20\(map\).md)|[operator\<\= \(multimap\)](../Topic/operator%3C%20\(multimap\).md)|Comprueba si el objeto de asignación o asignación múltiple del lado izquierdo del operador es menor o igual que el objeto de asignación o asignación múltiple del lado derecho.|  
|[operator\=\= \(map\)](../Topic/operator%3C=%20\(map\).md)|[operator\=\= \(multimap\)](../Topic/operator%3C=%20\(multimap\).md)|Comprueba si el objeto de asignación o asignación múltiple del lado izquierdo del operador es igual que el objeto de asignación o asignación múltiple del lado derecho.|  
|[operator\> \(map\)](../Topic/operator%3E%20\(map\).md)|[operator\> \(multimap\)](../Topic/operator%3E%20\(multimap\).md)|Comprueba si el objeto de asignación o asignación múltiple del lado izquierdo del operador es mayor que el objeto de asignación o asignación múltiple del lado derecho.|  
|[operator\>\= \(map\)](../Topic/operator%3E=%20\(map\).md)|[operator\>\= \(multimap\)](../Topic/operator%3E=%20\(multimap\).md)|Comprueba si el objeto de asignación o asignación múltiple del lado izquierdo del operador es mayor o igual que el objeto de asignación o asignación múltiple del lado derecho.|  
  
### Funciones de plantilla especializadas  
  
|Versión de asignación|Versión de asignación múltiple|Descripción|  
|---------------------------|------------------------------------|-----------------|  
|[swap \(map\)](../Topic/swap%20\(map\).md)|[swap \(multimap\)](../Topic/swap%20\(multimap\).md)|Intercambia los elementos de dos asignaciones o asignaciones múltiples.|  
  
### Clases  
  
|||  
|-|-|  
|[value\_compare \(Clase\)](../standard-library/value-compare-class-map.md)|Proporciona un objeto de función que puede comparar los elementos de una asignación comparando los valores de sus claves para determinar su orden relativo en la asignación.|  
|[map \(Clase\)](../standard-library/map-class.md)|Se usa para el almacenamiento y la recuperación de datos de una colección en la que cada uno de los elementos tiene una clave única con la que se ordenan automáticamente los datos.|  
|[multimap \(Clase\)](../standard-library/multimap-class.md)|Se usa para el almacenamiento y la recuperación de datos de una colección en la que cada uno de los elementos tiene una clave con la que se ordenan automáticamente los datos y no es necesario que las claves tengan valores únicos.|  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)