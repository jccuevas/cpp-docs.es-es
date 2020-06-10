---
title: add_rvalue_reference (clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_rvalue_reference
helpviewer_keywords:
- add_rvalue_reference Class
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
ms.openlocfilehash: 6d7cc1d45ed3b963de0a0a004c1696ddbf0af440
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623922"
---
# <a name="add_rvalue_reference-class"></a>add_rvalue_reference (clase)

Si es un tipo de objeto o función, crea un tipo de referencia a un valor R del parámetro de plantilla. De lo contrario, debido a la semántica de contracción de referencias, el tipo es el mismo que el parámetro de plantilla.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct add_rvalue_reference;

template <class T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```

### <a name="parameters"></a>Parámetros

*H*\
Tipo que se va a modificar.

## <a name="remarks"></a>Observaciones

La `add_rvalue_reference` clase tiene un miembro denominado `type` , que es un alias para el tipo de una referencia rvalue al parámetro de plantilla *T*. La semántica de la contracción de referencia implica que, para los tipos de no objeto y que no son de función *t*, `T&&` es una *t*. Por ejemplo, cuando *T* es un tipo de referencia de valor l, `add_rvalue_reference<T>::type` es el tipo de referencia de valor l, no una referencia rvalue.

Para mayor comodidad, \<type_traits> define una plantilla de aplicación auxiliar, `add_rvalue_reference_t` , que tiene un alias para el `type` miembro de `add_rvalue_reference` .

## <a name="example"></a>Ejemplo

En este ejemplo de código se usa static_assert para mostrar cómo se crean tipos de referencia a un valor R mediante `add_rvalue_reference` y `add_rvalue_reference_t` y cómo el resultado de `add_rvalue_reference` en un tipo de referencia a un valor R no es una referencia a un valor R, sino que se contrae en el tipo de referencia a un valor L.

```cpp
// ex_add_rvalue_reference.cpp
// Build by using: cl /EHsc /W4 ex_add_rvalue_reference.cpp
#include <type_traits>
#include <iostream>
#include <string>

using namespace std;
int main()
{
    static_assert(is_same<add_rvalue_reference<string>::type, string&&>::value,
        "Expected add_rvalue_reference_t<string> to be string&&");
    static_assert(is_same<add_rvalue_reference_t<string*>, string*&&>::value,
        "Expected add_rvalue_reference_t<string*> to be string*&&");
    static_assert(is_same<add_rvalue_reference<string&>::type, string&>::value,
        "Expected add_rvalue_reference_t<string&> to be string&");
    static_assert(is_same<add_rvalue_reference_t<string&&>, string&&>::value,
        "Expected add_rvalue_reference_t<string&&> to be string&&");
    cout << "All static_assert tests of add_rvalue_reference passed." << endl;
    return 0;
}

/*Output:
All static_assert tests of add_rvalue_reference passed.
*/
```

## <a name="requirements"></a>Requisitos

Encabezado: \<type_traits>

Espacio de nombres: std

## <a name="see-also"></a>Consulte también

[<type_traits>](type-traits.md)\
[add_lvalue_reference (clase)](add-lvalue-reference-class.md)\
[is_rvalue_reference (clase)](is-rvalue-reference-class.md)
