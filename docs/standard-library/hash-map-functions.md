---
title: Funciones de &lt;hash_map&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
caps.latest.revision: 9
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 394a9ffe15c256a43cdf16ffd164f2e907ab0535
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="lthashmapgt-functions"></a>Funciones de &lt;hash_map&gt;
|||  
|-|-|  
|[swap](#swap)|[swap (hash_map)](#swap_hash_map)|  
  
##  <a name="swap_hash_map"></a>  swap (hash_map)  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Intercambia los elementos de dos objetos hash_map.  
  
```
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 Objeto hash_map cuyos elementos se van a intercambiar con los del objeto map `left`.  
  
 `left`  
 Objeto hash_map cuyos elementos se van a intercambiar con los del objeto map `right`.  
  
### <a name="remarks"></a>Comentarios  
 La función de plantilla es un algoritmo especializado en la clase contenedora hash_map para ejecutar la función miembro `left.`[swap](../standard-library/basic-ios-class.md#swap)*(right*). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla **template \<class T> void swap(T&, T&)** del archivo de encabezado de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada de cada contenedor es mucho más rápida, dado que puede funcionar con la representación interna de la clase contenedora.  
  
 En Visual C++ .NET 2003, los miembros de los archivos de encabezado [<hash_map>](../standard-library/hash-map.md) y [<hash_set>](../standard-library/hash-set.md) ya no están en el espacio de nombres std, sino que se han movido al espacio de nombres stdext. Vea [The stdext Namespace](../standard-library/stdext-namespace.md) (El espacio de nombres stdext) para obtener más información.  
  
##  <a name="swap"></a>  swap  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_multimap](../standard-library/unordered-multimap-class.md).  
  
 Intercambia los elementos de dos objetos hash_multimap.  
  
```
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 Objeto hash_multimap cuyos elementos se van a intercambiar con los del objeto map `left`.  
  
 `left`  
 Objeto hash_multimap cuyos elementos se van a intercambiar con los del objeto map `right`.  
  
### <a name="remarks"></a>Comentarios  
 La función de plantilla es un algoritmo especializado en la clase contenedora hash_multimap para ejecutar la función miembro `left.`[swap](../standard-library/hash-multimap-class.md#swap)*(right*`)`. Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla **template \<class T> void swap(T&, T&)** del archivo de encabezado de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada de cada contenedor es mucho más rápida, dado que puede funcionar con la representación interna de la clase contenedora.  
  
 En Visual C++ .NET 2003, los miembros de los archivos de encabezado [<hash_map>](../standard-library/hash-map.md) y [<hash_set>](../standard-library/hash-set.md) ya no están en el espacio de nombres std, sino que se han movido al espacio de nombres stdext. Vea [The stdext Namespace](../standard-library/stdext-namespace.md) (El espacio de nombres stdext) para obtener más información.  
  
## <a name="see-also"></a>Vea también  
 [<hash_map>](../standard-library/hash-map.md)




