---
title: "bidirectional_iterator_tag (Struct) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xutility/std::bidirectional_iterator_tag"
  - "std::bidirectional_iterator_tag"
  - "std.bidirectional_iterator_tag"
  - "bidirectional_iterator_tag"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bidirectional_iterator_tag (clase)"
  - "bidirectional_iterator_tag (struct)"
ms.assetid: 9ac06066-b8ae-44b6-bee4-b05855f6a31a
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# bidirectional_iterator_tag (Struct)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una clase que proporciona un tipo de valor devuelto de la función de **iterator\_category** que representa un iterador bidireccional.  
  
## Sintaxis  
  
```  
  
   struct bidirectional_iterator_tag  
: public forward_iterator_tag {};  
```  
  
## Comentarios  
 Las clases de etiquetas de categoría se utilizan como etiquetas de compilación para la selección del algoritmo.  La función de plantilla debe encontrar la categoría más específica del argumento de iterador, para poder usar el algoritmo más eficaz en tiempo de compilación.  Para cada iterador de `Iterator`tipo, el ::\<**iterator\_category** de `iterator_traits``Iterator`\>se debe definir para ser la etiqueta más específica de la categoría que describe el comportamiento del iterador.  
  
 El tipo es igual que el ::\<**iterator\_category** de **iteratorIter**\>cuando **Iter** describe un objeto que puede actuar como iterador bidireccional.  
  
## Ejemplo  
 Vea [random\_access\_iterator\_tag](../standard-library/random-access-iterator-tag-struct.md) para obtener un ejemplo de cómo utilizar `bidirectional_iterator_tag`.  
  
## Requisitos  
 **Encabezado:** \<iterator\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [forward\_iterator\_tag \(Struct\)](../standard-library/forward-iterator-tag-struct.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)