---
title: licencia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.licensed
dev_langs:
- C++
helpviewer_keywords:
- licensed attribute
ms.assetid: 09cf3b4a-d3f2-43e3-9180-d420333b23bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b30a9a0e2d959725b5f5d94118493ef833a57579
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604834"
---
# <a name="licensed"></a>licensed

Indica que el objeto COM al que se aplica tiene licencia y se debe crear instancias mediante `IClassFactory2`.

## <a name="syntax"></a>Sintaxis

```cpp
[licensed]
```

## <a name="remarks"></a>Comentarios

El **licencia** atributo de C++ tiene la misma funcionalidad que el [licencia](http://msdn.microsoft.com/library/windows/desktop/aa367070) atributo MIDL.

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_licensed.cpp
// compile with: /LD
#include "unknwn.h"
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI : IUnknown {
   HRESULT f();
};

[coclass, version("2.1"), uuid(12345678-1111-2222-3333-123456789012),
licensed, threading(free), progid(some.name)]
class CSample : public IMyI {
public:
   int nSize;
};

[module(name="MyLibrary", version="1.0", helpstring="My Library Block")];
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|`coclass`|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)  
[Atributos de clase](../windows/class-attributes.md)  