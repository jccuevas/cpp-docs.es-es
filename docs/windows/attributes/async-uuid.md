---
title: async_uuid (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.async_uuid
helpviewer_keywords:
- async_uuid attribute
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
ms.openlocfilehash: 537bd6d645532d9d5d20b740125c66f3953239bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168465"
---
# <a name="async_uuid"></a>async_uuid

Especifica el UUID que dirige el compilador MIDL para definir versiones sincrónicas y asincrónicas de una interfaz COM.

## <a name="syntax"></a>Sintaxis

```cpp
[async_uuid (uuid)]
```

### <a name="parameters"></a>Parámetros

*uuid*<br/>
UUID que identifica la versión de la interfaz.

## <a name="remarks"></a>Observaciones

El atributo **async_uuid** C++ tiene la misma funcionalidad que el atributo MIDL [async_uuid](/windows/win32/Midl/async-uuid) .

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_async_uuid.cpp
// compile with: /LD
#include <Windows.h>
[module(name="Test")];
[object, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb"),
async_uuid("e8583106-38fd-487e-912e-4fc8645c677e")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|`interface`|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|**dual**, **dispinterface**|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de interfaz](interface-attributes.md)
