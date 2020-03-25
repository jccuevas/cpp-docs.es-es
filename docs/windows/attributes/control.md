---
title: control (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.control
helpviewer_keywords:
- Control attribute
ms.assetid: 3d046bb2-4afe-4cb8-a762-233b296e1975
ms.openlocfilehash: 9cdcca6fac2a92bf28f0f655489e61dcb08213e4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214947"
---
# <a name="control"></a>control

Especifica que el tipo definido por el usuario es un control.

## <a name="syntax"></a>Sintaxis

```cpp
[control]
```

## <a name="remarks"></a>Observaciones

El atributo de **control** implica el atributo [CoClass](coclass.md) . El atributo **control** C++ tiene la misma funcionalidad que el atributo MIDL del [control](/windows/win32/Midl/control) .

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_control.cpp
// compile with: /LD
#include <windows.h>
[module(name="Test", control=true)];

[object, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};

[coclass, control, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
class CTest : public ICustom {};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de clase](class-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)
