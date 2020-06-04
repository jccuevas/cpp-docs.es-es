---
title: Case (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.case
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
ms.openlocfilehash: da72fff3bb600b5db2fba0ecdfe9c6a768836f3c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167346"
---
# <a name="case-c"></a>case (C++)

Se usa con el [switch_type](switch-type.md) atributo de una **Unión**.

## <a name="syntax"></a>Sintaxis

```cpp
[ case(value) ]
```

#### <a name="parameters"></a>Parámetros

*value*<br/>
Un valor de entrada posible para el que desea proporcionar el procesamiento. El tipo de **valor** puede ser uno de los siguientes tipos:

- `int`

- `char`

- `boolean`

- `enum`

o un identificador de este tipo.

## <a name="remarks"></a>Observaciones

El atributo **Case** C++ tiene la misma funcionalidad que el atributo MIDL de **Case** . Este atributo solo se utiliza con el atributo [switch_type](switch-type.md) .

## <a name="example"></a>Ejemplo

En el código siguiente se muestra el uso del atributo **Case** :

```cpp
// cpp_attr_ref_case.cpp
// compile with: /LD
#include <unknwn.h>
[export]
struct SizedValue2 {
   [switch_type(char), switch_is(kind)] union {
      [case(1), string]
          wchar_t* wval;
      [default, string]
          char* val;
   };
    char kind;
};
[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Miembro de una **clase** o **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributos de clase](class-attributes.md)
