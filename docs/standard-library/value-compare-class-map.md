---
title: value_compare (Clase) (&lt;asignación&gt;)
ms.date: 11/04/2016
f1_keywords:
- std::value_compare
- std.value_compare
- map/std::value_compare
helpviewer_keywords:
- std::value_compare
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
ms.openlocfilehash: 1f872edce6f0114be7c90a8108ba248fd793a989
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447584"
---
# <a name="value_compare-class-ltmapgt"></a>value_compare (Clase) (&lt;asignación&gt;)

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

## <a name="remarks"></a>Observaciones

El criterio de comparación proporcionado por `value_compare` entre `value_types` de elementos completos contenidos en una asignación se induce de una comparación entre las claves de los elementos respectivos mediante la construcción de la clase auxiliar. El operador de función miembro utiliza el `comp` de objeto de tipo `key_compare` almacenado en el objeto de función proporcionado por `value_compare` para comparar los componentes de clave de ordenación de dos elementos.

Para conjuntos y conjuntos múltiples, que son simples contenedores donde los valores de clave son idénticos a los valores de elemento, `value_compare` es equivalente a `key_compare`. No lo es para asignaciones y asignaciones múltiples, dado que el valor de los elementos de tipo `pair` no es idéntico al valor de clave del elemento.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [value_comp](../standard-library/map-class.md#value_comp) para obtener un ejemplo de cómo declarar y usar `value_compare`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> de asignación

**Espacio de nombres:** std

## <a name="see-also"></a>Consulte también

[binary_function (Struct)](../standard-library/binary-function-struct.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
