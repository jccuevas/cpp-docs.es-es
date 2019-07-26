---
title: value_compare (Clase) (&lt;asignación&gt;)
ms.date: 11/04/2016
f1_keywords:
- std::value_compare
- std.value_compare
- map/std::value_compare
- value_compare
helpviewer_keywords:
- std::value_compare
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
ms.openlocfilehash: d098e947aec1ea543f29c168a632d1f4c9412e82
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448323"
---
# <a name="valuecompare-class-ltmapgt"></a>value_compare (Clase) (&lt;asignación&gt;)

Proporciona un objeto de función que puede comparar los elementos de una asignación comparando los valores de sus claves para determinar su orden relativo en la asignación.

## <a name="syntax"></a>Sintaxis

```cpp
class value_compare : public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(const value_type& left, const value_type& right) const;
    value_compare(key_compare pred) : comp(pred);
protected:
    key_compare comp;
};
```

## <a name="remarks"></a>Comentarios

El criterio de comparación proporcionado `value_compare` por `value_types` entre todos los elementos contenidos en una asignación se induce de una comparación entre las claves de los elementos respectivos mediante la construcción de la clase auxiliar. El operador de función miembro utiliza el `comp` objeto de `key_compare` tipo almacenado en el objeto de función `value_compare` proporcionado por para comparar los componentes de clave de ordenación de dos elementos.

Para conjuntos y conjuntos múltiples, que son simples contenedores donde los valores de clave son idénticos a los valores de elemento, `value_compare` es equivalente a `key_compare`. No lo es para asignaciones y asignaciones múltiples, dado que el valor de los elementos de tipo `pair` no es idéntico al valor de clave del elemento.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [value_comp](../standard-library/map-class.md#value_comp) para obtener un ejemplo de cómo declarar y usar `value_compare`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<map>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[binary_function (Struct)](../standard-library/binary-function-struct.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
