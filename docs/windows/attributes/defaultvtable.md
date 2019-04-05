---
title: defaultvtable (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultvtable
helpviewer_keywords:
- defaultvtable attribute
ms.assetid: 5b3ed483-f69e-44dd-80fc-952028eb9d73
ms.openlocfilehash: 813fb9dd4edf2f6e522e7310ba1e8bfcd55ed2b9
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028352"
---
# <a name="defaultvtable"></a>defaultvtable

Define una interfaz que la interfaz de vtable predeterminada para un objeto COM.

## <a name="syntax"></a>Sintaxis

```cpp
[ defaultvtable(interface) ]
```

### <a name="parameters"></a>Parámetros

*interfaz*<br/>
La interfaz designada que se desea tener la vtable predeterminado para el objeto COM.

## <a name="remarks"></a>Comentarios

El **defaultvtable** atributo de C++ tiene la misma funcionalidad que el [defaultvtable](/windows/desktop/Midl/defaultvtable) atributo MIDL.

## <a name="example"></a>Ejemplo

El código siguiente muestra los atributos en una clase que utilice **defaultvtable** para especificar una interfaz predeterminada:

```cpp
// cpp_attr_ref_defaultvtable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI1 {
   HRESULT x();
};

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface IMyI2 {
   HRESULT x();
};

[object, uuid("00000000-0000-0000-0000-000000000003")]
__interface IMyI3 {
   HRESULT x();
};

[coclass, source(IMyI3, IMyI1), default(IMyI3, IMyI2), defaultvtable(IMyI1),
uuid("00000000-0000-0000-0000-000000000004")]
class CMyC3 : public IMyI3 {};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|**coclase**|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de clase](class-attributes.md)