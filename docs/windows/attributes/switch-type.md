---
title: switch_type (C++ atributo COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.switch_type
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
ms.openlocfilehash: b461769d3d988efae0be7380e1e0112e3f3cf801
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407125"
---
# <a name="switchtype"></a>switch_type

Identifica el tipo de la variable utilizada como la unión discriminante.

## <a name="syntax"></a>Sintaxis

```cpp
[switch_type(
type
}]
```

### <a name="parameters"></a>Parámetros

*type*<br/>
El tipo de conmutador, puede ser un tipo entero, carácter, un valor booleano o enumeración.

## <a name="remarks"></a>Comentarios

El **switch_type** C++ atributo tiene la misma funcionalidad que el [switch_type](/windows/desktop/Midl/switch-type) atributo MIDL.

Atributos de C++ no admiten [encapsulado uniones](/windows/desktop/Midl/encapsulated-unions). [Uniones nonencapsulated](/windows/desktop/Midl/nonencapsulated-unions) solo se admiten en el formato siguiente:

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

Consulte la [caso](case-cpp.md) ejemplo para un ejemplo de uso de **switch_type**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**typedef**|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[export](export.md)