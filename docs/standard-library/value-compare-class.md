---
title: value_compare (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- value_compare
dev_langs:
- C++
helpviewer_keywords:
- value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f46153400744b4a6d0350b97fa7158ea9f69c34
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957113"
---
# <a name="valuecompare-class"></a>value_compare (Clase)

Proporciona un objeto de función que puede comparar los elementos de hash_map al comparar los valores de sus claves para determinar su orden relativo en hash_map.

## <a name="syntax"></a>Sintaxis

```cpp
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

Los criterios de comparación proporcionados por value_compare entre `value_types` de elementos enteros incluidos en un objeto hash_map se induce de una comparación entre las claves de los respectivos elementos mediante la construcción de la clase auxiliar. El operador de la función miembro usa el objeto `comp` de tipo `key_compare` almacenado en el objeto de función proporcionado por value_compare para comparar los componentes clave de ordenación de dos elementos.

Para hash_set y hash_multiset, que son simples contenedores donde los valores de clave son idénticos a los valores de elemento, value_compare es equivalente a `key_compare`. No lo es para hash_map y hash_multimap, dado que el valor de los elementos de tipo `pair` no es idéntico al valor de clave del elemento.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [hash_map::value_comp](../standard-library/hash-map-class.md#value_comp) para obtener un ejemplo de cómo declarar y usar value_compare.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<hash_map>

**Espacio de nombres:** stdext

## <a name="see-also"></a>Vea también

[binary_function (Struct)](../standard-library/binary-function-struct.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
