---
title: "output_iterator_tag (Struct) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::output_iterator_tag"
  - "output_iterator_tag"
  - "xutility/std::output_iterator_tag"
  - "std.output_iterator_tag"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "output_iterator_tag (clase)"
  - "output_iterator_tag (struct)"
ms.assetid: c23a4331-b069-4fa0-9c3a-1c9be7095553
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# output_iterator_tag (Struct)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase que proporciona un tipo de valor devuelto para una función **iterator\_category** que representa un iterador de salida.  
  
## Sintaxis  
  
```  
  
struct output_iterator_tag {};  
  
```  
  
## Comentarios  
 Las clases de etiquetas de categoría se usan como etiquetas para la selección de algoritmo de compilación. La función de plantilla debe buscar la categoría más específica de su argumento de iterador para que pueda usar el algoritmo más eficaz en tiempo de compilación. Para cada iterador del tipo `Iterator`, `iterator_traits`\<`Iterator`\>**:: iterator\_category** debe definirse para que sea la etiqueta de categoría más específica que describe el comportamiento del iterador.  
  
 El tipo es igual a **iterador**\<**Iter**\>**:: iterator\_category** cuando **Iter** describe un objeto que puede actuar como un iterador de salida.  
  
 Esta etiqueta no se parametriza en la `value_type` o `difference_type` para el iterador, al igual que con las etiquetas de iterador, porque los iteradores de salida no tienen un `value_type` o un `difference_type`.  
  
## Ejemplo  
 Consulte [iterator\_traits](../standard-library/iterator-traits-struct.md) o [random\_access\_iterator\_tag](../standard-library/random-access-iterator-tag-struct.md) para obtener un ejemplo de cómo usar **iterator\_tag**s.  
  
## Requisitos  
 **Encabezado:** \<iterator\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)