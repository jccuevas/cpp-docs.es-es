---
title: async_uuid | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.async_uuid
dev_langs:
- C++
helpviewer_keywords:
- async_uuid attribute
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7619868e131476143c144e695e842708d1b54a6b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606450"
---
# <a name="asyncuuid"></a>async_uuid

Especifica el UUID que indica al compilador MIDL para definir las versiones sincrónicas y asincrónicas de una interfaz COM.

## <a name="syntax"></a>Sintaxis

```cpp
[async_uuid (
   uuid
)]
```

### <a name="parameters"></a>Parámetros

*uuid*  
Un UUID que identifica la versión de la interfaz.

## <a name="remarks"></a>Comentarios

El **async_uuid** atributo de C++ tiene la misma funcionalidad que el [async_uuid](http://msdn.microsoft.com/library/windows/desktop/aa366735) atributo MIDL.

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
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|**dual**, **dispinterface**|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)  
[Atributos de interfaz](../windows/interface-attributes.md)  