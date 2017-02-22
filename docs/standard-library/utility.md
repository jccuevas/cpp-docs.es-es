---
title: "&lt;utility&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<utility>"
  - "utility/std::<utility>"
  - "std.<utility>"
  - "std::<utility>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "utility (encabezado)"
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# &lt;utility&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define los tipos, funciones y operadores de las bibliotecas de plantillas estándar \(STL\) que ayudan a crear y administrar pares de objetos, que resultan útiles cuando se deben tratar dos objetos como si fueran uno solo.  
  
## Sintaxis  
  
```  
  
#include <utility>  
  
```  
  
## Comentarios  
 Los pares se usan ampliamente en la biblioteca estándar de C\+\+.  Son necesarios como argumentos y valores de devolución para distintas funciones y como tipos de elemento para contenedores como [la clase map](../standard-library/map-class.md) y la [clase multimap](../standard-library/multimap-class.md).  \<map\> incluye automáticamente el encabezado \<utility\> para ayudar en la administración de los elementos de tipo de par clave\/valor.  
  
### Clases  
  
|||  
|-|-|  
|[tuple\_element](../standard-library/tuple-element-class-utility.md)|Clase que contiene el tipo de un elemento `pair`.|  
|[tuple\_size](../standard-library/tuple-size-class-utility.md)|Clase que contiene el recuento de elementos `pair`.|  
  
### Funciones  
  
|||  
|-|-|  
|[forward](../Topic/forward.md)|Impide que el reenvío directo oculte el tipo de referencia \(`lvalue` o `rvalue`\) del argumento.|  
|[obtener](../Topic/get%20Function%20%3Cutility%3E.md)|Función que obtiene un elemento de un objeto `pair`.|  
|[make\_pair](../Topic/make_pair.md)|Función de aplicación auxiliar de plantilla usada para construir objetos de tipo `pair`, donde los tipos de componente se basan en los tipos de datos pasados como parámetros.|  
|[mover](../Topic/move.md)|Devuelve los argumentos pasados como referencia `rvalue`.|  
|[swap](../Topic/swap%20\(%3Cutility%3E\).md)|Intercambia los elementos de dos objetos `pair`.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\!\=](../Topic/operator!=%20\(%3Cutility%3E\).md)|Comprueba si el objeto de par del lado izquierdo del operador no es igual que el objeto de par del lado derecho.|  
|[operator\=\=](../Topic/operator==%20\(%3Cutility%3E\).md)|Comprueba si el objeto de par del lado izquierdo del operador es igual que el objeto de par del lado derecho.|  
|[operador \<](../Topic/operator%3C%20\(%3Cutility%3E\).md)|Comprueba si el objeto de par del lado izquierdo del operador es menor que el objeto de par del lado derecho.|  
|[operator\<\=](../Topic/operator%3C=%20\(%3Cutility%3E\).md)|Comprueba si el objeto de par del lado izquierdo del operador es menor o igual que el objeto de par del lado derecho.|  
|[operador \>](../Topic/operator%3E%20\(%3Cutility%3E\).md)|Comprueba si el objeto de par del lado izquierdo del operador es mayor que el objeto de par del lado derecho.|  
|[operator\>\=](../Topic/operator%3E=%20\(%3Cutility%3E\).md)|Comprueba si el objeto de par del lado izquierdo del operador es mayor o igual que el objeto de par del lado derecho.|  
  
### Structs  
  
|||  
|-|-|  
|[identidad](../standard-library/identity-structure.md)||  
|[pair](../standard-library/pair-structure.md)|Tipo que proporciona la capacidad de tratar dos objetos como uno solo.|  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)