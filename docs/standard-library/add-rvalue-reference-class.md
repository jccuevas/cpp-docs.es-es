---
title: add_rvalue_reference (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::add_rvalue_reference
dev_langs:
- C++
helpviewer_keywords:
- add_rvalue_reference Class
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4936772c82bb482e468a37f2f7b327c9a728f0c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720127"
---
# <a name="addrvaluereference-class"></a>add_rvalue_reference (clase)

Si es un tipo de objeto o función, crea un tipo de referencia a un valor R del parámetro de plantilla. De lo contrario, debido a la semántica de contracción de referencias, el tipo es el mismo que el parámetro de plantilla.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct add_rvalue_reference;

template <class T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo que se va a modificar.

## <a name="remarks"></a>Comentarios

El `add_rvalue_reference` clase tiene un miembro denominado `type`, que es un alias para el tipo de referencia rvalue para el parámetro de plantilla *T*. La semántica de contracción de referencias implica que, para los tipos que no sean de objeto y que no son de función *T*, `T&&` es un *T*. Por ejemplo, cuando *T* es un tipo de referencia lvalue, `add_rvalue_reference<T>::type` es el tipo de referencia de valor l, no una referencia rvalue.

Para mayor comodidad, \<type_traits > define una plantilla de aplicación auxiliar, `add_rvalue_reference_t`, ese alias el `type` miembro de `add_rvalue_reference`.

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

Encabezado: \<type_traits >

Namespace: std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[add_lvalue_reference (Clase)](../standard-library/add-lvalue-reference-class.md)<br/>
[is_rvalue_reference (Clase)](../standard-library/is-rvalue-reference-class.md)<br/>
