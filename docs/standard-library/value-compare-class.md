---
title: value_compare (Clase)
ms.date: 11/04/2016
f1_keywords:
- value_compare
helpviewer_keywords:
- value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
ms.openlocfilehash: 0e057a6229c903402a51b34a8f4e844e80ace187
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452365"
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

Los criterios de comparación proporcionados por `value_types` value_compare entre todos los elementos contenidos en un hash_map se inducen de una comparación entre las claves de los elementos respectivos mediante la construcción de la clase auxiliar. El operador de función miembro usa el `comp` objeto de `key_compare` tipo almacenado en el objeto de función proporcionado por value_compare para comparar los componentes de clave de ordenación de dos elementos.

Para hash_set y hash_multiset, que son simples contenedores donde los valores de clave son idénticos a los valores de elemento, value_compare es equivalente a `key_compare`. No lo es para hash_map y hash_multimap, dado que el valor de los elementos de tipo `pair` no es idéntico al valor de clave del elemento.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [hash_map::value_comp](../standard-library/hash-map-class.md#value_comp) para obtener un ejemplo de cómo declarar y usar value_compare.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<hash_map>

**Espacio de nombres:** stdext

## <a name="see-also"></a>Vea también

[binary_function (Struct)](../standard-library/binary-function-struct.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
