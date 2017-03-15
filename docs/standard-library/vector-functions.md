---
title: Funciones de &lt;vector&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6cdcf043-eef6-4330-83f0-4596fb9f968a
caps.latest.revision: 10
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: bb62c0c4e5b2965438539b17ec5a2c465e647ed7
ms.lasthandoff: 02/24/2017

---
# <a name="ltvectorgt-functions"></a>Funciones de &lt;vector&gt;

  
##  <a name="a-nameswapa--swap"></a><a name="swap"></a>  swap  
 Intercambia los elementos de dos vectores.  
  
```  
template <class Type, class Allocator>  
void swap(vector<Type, Allocator>& left, vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 El vector que proporciona los elementos que se van a intercambiar o el vector cuyos elementos se van a intercambiar con los del vector ` left`.  
  
 ` left`  
 El vector cuyos elementos se van a intercambiar con los del vector ` right`.  
  
### <a name="remarks"></a>Comentarios  
 La función de plantilla es un algoritmo especializado en la clase contenedora de vector establecida para ejecutar la función miembro ` left.` [vector::swap](../standard-library/vector-class.md) *( right*). Se trata de instancias de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, entonces el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla **template** \< **class T**> **void swap**( **T&**, **T&**), en la clase de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada de cada contenedor es mucho más rápida, dado que puede funcionar con la representación interna de la clase contenedora.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de código para la función miembro [vector::swap](../standard-library/vector-class.md) para obtener un ejemplo que usa la versión de la plantilla de `swap`.  
  
## <a name="see-also"></a>Vea también  
 [\<vector>](../standard-library/vector.md)


