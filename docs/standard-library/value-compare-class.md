---
title: value_compare (clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: value_compare
dev_langs: C++
helpviewer_keywords: value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a340acbc50c629686f010f51ce07e397e4084154
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="valuecompare-class"></a>value_compare (Clase)
Proporciona un objeto de función que puede comparar los elementos de hash_map al comparar los valores de sus claves para determinar su orden relativo en hash_map.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class value_compare
 : std::public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(
    const value_type& left,
    const value_type& right) const
 {
    return (comp(left.first, right.first));

 }
protected:
    value_compare(const key_compare& c) : comp (c) { }
    key_compare comp;
};
```  
  
## <a name="remarks"></a>Comentarios  
 El criterio de comparación proporcionado por value_compare entre **value_types** de elementos enteros incluidos en una hash_map se induce de una comparación entre las claves de los respectivos elementos mediante la construcción de la clase auxiliar. El operador de la función miembro usa el objeto **comp** de tipo `key_compare` almacenado en el objeto de función proporcionado por value_compare para comparar los componentes de clave de ordenación de dos elementos.  
  
 Para hash_set y hash_multiset, que son simples contenedores donde los valores de clave son idénticos a los valores de elemento, value_compare es equivalente a `key_compare`. No lo es para hash_map y hash_multimap, dado que el valor de los elementos de tipo `pair` no es idéntico al valor de clave del elemento.  
  
   
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [hash_map::value_comp](../standard-library/hash-map-class.md#value_comp) para obtener un ejemplo de cómo declarar y usar value_compare.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<hash_map>  
  
 **Espacio de nombres:** stdext  
  
## <a name="see-also"></a>Vea también  
 [binary_function (Struct)](../standard-library/binary-function-struct.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)



