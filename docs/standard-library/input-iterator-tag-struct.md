---
title: "input_iterator_tag (Struct) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "input_iterator_tag"
  - "std.input_iterator_tag"
  - "std::input_iterator_tag"
  - "xutility/std::input_iterator_tag"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "input_iterator_tag (clase)"
  - "input_iterator_tag (struct)"
ms.assetid: ad68a4c6-f315-4ce1-8b74-c1fc71bd1577
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# input_iterator_tag (Struct)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una clase que proporciona un tipo de valor devuelto de la función de **iterator\_category** que representa un iterador de entrada.  
  
## Sintaxis  
  
```  
  
struct input_iterator_tag {};  
  
```  
  
## Comentarios  
 Las clases de etiquetas de categoría se utilizan como etiquetas de compilación para la selección del algoritmo.  La función de plantilla debe encontrar la categoría más específica del argumento de iterador para poder usar el algoritmo más eficaz en tiempo de compilación.  Para cada iterador de `Iterator`escrito, `iterator_traits`\<`Iterator`\>**::iterator\_category** se debe definir para ser la etiqueta más específica de la categoría que describe el comportamiento del iterador.  
  
 El tipo es igual que **iterator**\<**Iter**\>**::iterator\_category** cuando **Iter** describe un objeto que puede actuar como iterador de la entrada.  
  
## Ejemplo  
 Vea [iterator\_traits](../standard-library/iterator-traits-struct.md) o [random\_access\_iterator\_tag](../standard-library/random-access-iterator-tag-struct.md) para obtener un ejemplo de cómo utilizar s para **iterator\_tag**.  
  
## Requisitos  
 **Encabezado:** \<iterator\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)