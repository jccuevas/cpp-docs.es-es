---
title: v1_enum (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.v1_enum
helpviewer_keywords:
- v1_enum attribute
ms.assetid: 2fe92d92-81b9-4a1c-b6ce-437d0eb770ca
ms.openlocfilehash: 08654eed7ad467dc22d2cbbf811c9169e5292f16
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024574"
---
# <a name="v1enum"></a>v1_enum

Indica que el tipo enumerado especificado se transmite como una entidad de 32 bits en lugar de con el valor predeterminado de 16 bits.

## <a name="syntax"></a>Sintaxis

```cpp
[v1_enum]
```

## <a name="remarks"></a>Comentarios

El **v1_enum** atributo de C++ tiene la misma funcionalidad que el [v1_enum](/windows/desktop/Midl/v1-enum) atributo MIDL.

## <a name="example"></a>Ejemplo

El código siguiente muestra un uso de **v1_enum**:

```cpp
// cpp_attr_ref_v1_enum.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export, v1_enum]
enum eList {
   e1 = 1, e2 = 2
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Tipo enumerado|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Typedef, Enum, Union y Struct (Atributos)](typedef-enum-union-and-struct-attributes.md)