---
title: switch_type (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.switch_type
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
ms.openlocfilehash: c3a4187c629238fa464a607c0b653f857fa44b6a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513948"
---
# <a name="switch_type"></a>switch_type

Identifica el tipo de la variable utilizada como discriminante de Unión.

## <a name="syntax"></a>Sintaxis

```cpp
[switch_type(
type
}]
```

### <a name="parameters"></a>Parámetros

*type*<br/>
El tipo de modificador puede ser un entero, un carácter, un valor booleano o un tipo de enumeración.

## <a name="remarks"></a>Comentarios

El atributo **switch_type** C++ tiene la misma funcionalidad que el atributo MIDL [switch_type](/windows/win32/Midl/switch-type) .

C++los atributos no admiten [uniones encapsuladas](/windows/win32/Midl/encapsulated-unions). Las [uniones no encapsuladas](/windows/win32/Midl/nonencapsulated-unions) solo se admiten en el formato siguiente:

```cpp
// cpp_attr_ref_switch_type.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLibrary")];
[ export ]
struct SizedValue2 {
   [switch_type("char"), switch_is(kind)] union {
      [case(1), string]
         wchar_t* wval;
      [default, string]
         char* val;
   };
   char kind;
};
```

## <a name="example"></a>Ejemplo

Vea el ejemplo de [caso](case-cpp.md) para ver un ejemplo de uso de **switch_type**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**typedef**|
|**Reiterativo**|Sin |
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[export](export.md)