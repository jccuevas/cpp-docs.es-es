---
title: "forward_iterator_tag (Struct) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.forward_iterator_tag"
  - "forward_iterator_tag"
  - "std::forward_iterator_tag"
  - "xutility/std::forward_iterator_tag"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "forward_iterator_tag (clase)"
  - "forward_iterator_tag (struct)"
ms.assetid: 68b633ac-b135-4e9e-837d-14248a262ec5
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# forward_iterator_tag (Struct)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una clase que proporciona un tipo de valor devuelto de la función de **iterator\_category** que representa un iterador hacia delante.  
  
## Sintaxis  
  
```  
  
   struct forward_iterator_tag  
: public input_iterator_tag {};  
```  
  
## Comentarios  
 Las clases de etiquetas de categoría se utilizan como etiquetas de compilación para la selección del algoritmo.  La función de plantilla debe averiguar cuál es la categoría más específica del argumento de iterador para poder usar el algoritmo más eficaz en tiempo de compilación.  Para cada iterador de `Iterator`escrito, `iterator_traits`\<`Iterator`\>**::iterator\_category** se debe definir para ser la etiqueta más específica de la categoría que describe el comportamiento del iterador.  
  
 El tipo es igual que **iterator**\<**Iter**\>**::iterator\_category** cuando **Iter** describe un objeto que puede actuar como iterador hacia delante.  
  
## Ejemplo  
 Vea [iterator\_traits](../standard-library/iterator-traits-struct.md) o [random\_access\_iterator\_tag](../standard-library/random-access-iterator-tag-struct.md) para obtener un ejemplo de cómo utilizar s para **iterator\_tag**.  
  
## Requisitos  
 **Encabezado:** \<iterator\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [input\_iterator\_tag \(Struct\)](../standard-library/input-iterator-tag-struct.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)