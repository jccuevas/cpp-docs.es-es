---
title: "initializer_list Class | Microsoft Docs"
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
ms.assetid: 1f2c0ff4-5636-4f79-b008-e75426e3d2ab
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# initializer_list Class
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Proporciona acceso a una matriz de elementos en la que cada miembro es del tipo especificado.  
  
## Sintaxis  
  
```cpp  
template<  
    class Type >  
    class initializer_list  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`_Elem`|Tipo de datos de elementos que se va a almacenar en la `initializer_list`.|  
|`_First`|Puntero al primer elemento de `initializer_list`.|  
|`_Last`|Puntero al último elemento de `initializer_list`.|  
  
## Comentarios  
 Se puede construir `initializer_list` con una lista de inicializadores entre llaves:  
  
```cpp  
initializer_list<int> i1{ 1, 2, 3, 4 };  
```  
  
 El compilador transforma las listas de inicializadores entre llaves con elementos homogéneos en una `initializer_list` siempre y cuando la signatura de la función requiera una `initializer_list`.  Para obtener información detallada sobre el uso de `initializer_list`, vea [Inicialización uniforme y constructores de delegación](../cpp/uniform-initialization-and-delegating-constructors.md).  
  
### Constructores  
  
|||  
|-|-|  
|[initializer\_list](../Topic/forward_list::forward_list.md)|Construye un objeto de tipo `initializer_list`.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|value\_type|Tipo de los elementos de `initializer_list`.|  
|referencia|Tipo que proporciona una referencia a un elemento de `initializer_list`.|  
|const\_reference|Tipo que proporciona una referencia constante a un elemento de `initializer_list`.|  
|size\_type|Tipo que representa el número de elementos de `initializer_list`.|  
|iterator|Tipo que proporciona un iterador para `initializer_list`.|  
|const\_iterator|Tipo que proporciona un iterador constante para `initializer_list`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[begin](../Topic/initializer_list::begin.md)|Devuelve un puntero al primer elemento de `initializer_list`.|  
|[end](../Topic/initializer_list::end.md)|Devuelve un puntero a un elemento más allá del último elemento de `initializer_list`.|  
|[size](../Topic/initializer_list::size.md)|Devuelve el número de elementos de `initializer_list`.|  
  
## Requisitos  
 **Encabezado:** \<initializer\_list\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<forward\_list\>](../standard-library/forward-list.md)