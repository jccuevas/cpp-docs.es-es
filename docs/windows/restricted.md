---
title: restringido | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.restricted
dev_langs:
- C++
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e8d226f508f5f5e8c717bd671413f21377c0ae01
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202295"
---
# <a name="restricted"></a>restricted

Especifica que un miembro de un módulo, interfaz o dispinterface no se puede llamar arbitrariamente.

## <a name="syntax"></a>Sintaxis

```cpp
[ restricted(
   interfaces
) ]
```

### <a name="parameters"></a>Parámetros

*interfaces*  
Una o más interfaces que no se llama de forma arbitraria en un objeto COM. Este parámetro solo es válido cuando se aplica a una clase.

## <a name="remarks"></a>Comentarios

El **restringido** atributo de C++ tiene la misma funcionalidad que el [restringido](/windows/desktop/Midl/restricted) atributo MIDL.

## <a name="example"></a>Ejemplo

El código siguiente muestra cómo usar el **restringido** atributo:

```cpp
// cpp_attr_ref_restricted.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface a
{
};

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface b
{
};

[coclass, restricted(a,b), uuid("00000000-0000-0000-0000-000000000003")]
class c : public a, public b
{
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Método, la interfaz **interfaz**, **clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|**coclase** (cuando se aplica a **clase** o **struct**)|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)  
[Atributos de interfaz](../windows/interface-attributes.md)  
[Atributos de método](../windows/method-attributes.md)  