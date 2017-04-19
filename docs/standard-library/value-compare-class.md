---
title: value_compare (clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- value_compare
dev_langs:
- C++
helpviewer_keywords:
- value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: c82ae35feadcf1f28af47d3f055e854f7bcf6a34
ms.lasthandoff: 02/24/2017

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
  
 En Visual C++ .NET 2003, los miembros de los archivos de encabezado [<hash_map>](../standard-library/hash-map.md) y [<hash_set>](../standard-library/hash-set.md) ya no están en el espacio de nombres std, sino que se han movido al espacio de nombres stdext. Vea [stdext (Espacio de nombres)](../standard-library/stdext-namespace.md) para obtener más información.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [hash_map::value_comp](../standard-library/hash-map-class.md#hash_map__value_comp) para obtener un ejemplo de cómo declarar y usar value_compare.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<hash_map>  
  
 **Espacio de nombres:** stdext  
  
## <a name="see-also"></a>Vea también  
 [binary_function (Struct)](../standard-library/binary-function-struct.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)




