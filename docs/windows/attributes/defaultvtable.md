---
title: defaultvtable (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultvtable
helpviewer_keywords:
- defaultvtable attribute
ms.assetid: 5b3ed483-f69e-44dd-80fc-952028eb9d73
ms.openlocfilehash: 8ab37af4deab516dc01f55f986811668737cf18c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501646"
---
# <a name="defaultvtable"></a>defaultvtable

Define una interfaz como la interfaz vtable predeterminada para un objeto COM.

## <a name="syntax"></a>Sintaxis

```cpp
[ defaultvtable(interface) ]
```

### <a name="parameters"></a>Parámetros

*interface*<br/>
La interfaz designada que desea que tenga la tabla vtable predeterminada para el objeto COM.

## <a name="remarks"></a>Comentarios

El atributo **defaultvtable** C++ tiene la misma funcionalidad que el atributo MIDL [defaultvtable](/windows/win32/Midl/defaultvtable) .

## <a name="example"></a>Ejemplo

En el código siguiente se muestran los atributos de una clase que usan **defaultvtable** para especificar una interfaz predeterminada:

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
|**Reiterativo**|Sin|
|**Atributos requeridos**|**coclase**|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de clase](class-attributes.md)