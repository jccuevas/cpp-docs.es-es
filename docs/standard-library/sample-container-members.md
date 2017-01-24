---
title: "Miembros de Sample Container | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases container"
ms.assetid: dc5a1998-a31b-4adf-b888-8abe5b87a4e0
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Miembros de Sample Container
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  Este tema está en la documentación de Visual C\+\+ como ejemplo no funcional de contenedores utilizados en la biblioteca estándar de C\+\+.  Para obtener más información, vea [Contenedores STL](../standard-library/stl-containers.md).  
  
## Referencia  
  
## Typedefs  
  
|||  
|-|-|  
|[const\_iterator](../standard-library/container-class-const-iterator.md)|Describe un objeto que puede actuar como iterador constante para la secuencia controlada.|  
|[const\_reference](../standard-library/container-class-const-reference.md)|Describe un objeto que puede actuar como referencia constante a un elemento de la secuencia controlada.|  
|[const\_reverse\_iterator](../standard-library/container-class-const-reverse-iterator.md)|Describe un objeto que puede actuar como iterador inverso constante para la secuencia controlada.|  
|[difference\_type](../standard-library/container-class-difference-type.md)|Describe un objeto que puede representar la diferencia entre las direcciones de los dos elementos de la secuencia controlada.|  
|[iterator](../standard-library/container-class-iterator.md)|Describe un objeto que puede actuar como iterador para la secuencia controlada.|  
|[reference](../standard-library/container-class-reference.md)|Describe un objeto que puede actuar como referencia a un elemento de la secuencia controlada.|  
|[reverse\_iterator](../standard-library/container-class-reverse-iterator.md)|Describe un objeto que puede actuar como iterador inverso para la secuencia controlada.|  
|[size\_type](../standard-library/container-class-size-type.md)|Describe un objeto que puede representar la longitud de cualquier secuencia controlada.|  
|[value\_type](../standard-library/container-class-value-type.md)|Representa un sinónimo para el parámetro **Ty**de la plantilla.|  
  
## Funciones miembro  
  
|||  
|-|-|  
|[begin](../standard-library/container-class-begin.md)|Devuelve un iterador que apunte al primer elemento de la secuencia \(o simplemente más allá del final de una secuencia vacía\).|  
|[clear](../standard-library/container-class-clear.md)|Llama a [barrido](../standard-library/container-class-erase.md)\( [inicio](../standard-library/container-class-begin.md), [final](../standard-library/container-class-end.md)\).|  
|[empty](../standard-library/container-class-empty.md)|Devuelve **true** para una secuencia controlada vacía.|  
|[end](../standard-library/container-class-end.md)|Devuelve un iterador que señala simplemente más allá del final de la secuencia.|  
|[erase](../standard-library/container-class-erase.md)|Borra un elemento.|  
|[max\_size](../standard-library/container-class-max-size.md)|Devuelve la longitud de la secuencia más larga que el objeto puede supervisar, de tiempo constante sin importar la longitud de la secuencia controlada.|  
|[rbegin](../standard-library/container-class-rbegin.md)|Devuelve un iterador inversa que elija simplemente más allá del final de la secuencia controlada, elija el principio de la secuencia inversa.|  
|[rend](../standard-library/container-class-rend.md)|La función miembro devuelve un iterador inversa que apunte al primer elemento de la secuencia \(o simplemente más allá del final de una secuencia vacía\), elija el final de la secuencia inversa.|  
|[size](../standard-library/container-class-size.md)|Devuelve la longitud de la secuencia controlada, en tiempo constante sin importar la longitud de la secuencia controlada.|  
|[swap](../standard-library/container-class-swap.md)|Cambia las secuencias controladas entre **\*this** y `_Right`.|