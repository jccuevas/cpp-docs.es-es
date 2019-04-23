---
title: ref (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.ref
helpviewer_keywords:
- ref attribute
ms.assetid: 67e82d3e-07d9-4ef8-bf2b-0a4491d12557
ms.openlocfilehash: f051fe577087d81515ddf0b44dfb15ad0fb2c616
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041382"
---
# <a name="ref-c"></a>ref (C++)

Identifica un puntero de referencia.

## <a name="syntax"></a>Sintaxis

```cpp
[ref]
```

## <a name="remarks"></a>Comentarios

El **ref** atributo de C++ tiene la misma funcionalidad que el [ref](/windows/desktop/Midl/ref) atributo MIDL.

## <a name="example"></a>Ejemplo

El código siguiente muestra cómo usar el **ref** atributo:

```cpp
// cpp_attr_ref_ref.cpp
// compile with: /LD
#include <windows.h>
[module(name="ATLFIRELib")];
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   [id(1), unique] char * GetFirstName([in, ref] char * pszFullName );
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**TypeDef**, parámetro de interfaz, el método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)