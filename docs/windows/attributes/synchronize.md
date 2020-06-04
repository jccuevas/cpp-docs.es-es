---
title: Synchronize (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.synchronize
helpviewer_keywords:
- synchronize attribute
ms.assetid: 15fc8544-955d-4765-b3d5-0f619c8b3f40
ms.openlocfilehash: a0f4702de4cfde8586cc573f9ff5a6195984d207
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214518"
---
# <a name="synchronize"></a>synchronize

Sincroniza el acceso al método de destino.

## <a name="syntax"></a>Sintaxis

```cpp
[synchronize]
```

## <a name="remarks"></a>Observaciones

El atributo **Synchronize** C++ implementa la compatibilidad para sincronizar el método de destino de un objeto. La sincronización permite que varios objetos usen un recurso común (por ejemplo, un método de una clase) controlando el acceso del método de destino.

El código insertado por este atributo llama al método `Lock` adecuado (determinado por el modelo de subprocesos) al principio del método de destino. Cuando se sale del método, se llama automáticamente a `Unlock`. Para obtener más información sobre estas funciones, vea [CComAutoThreadModule:: Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)

Este atributo requiere que el atributo [coclass](coclass.md), [progid](progid.md)o [vi_progid](vi-progid.md) (u otro atributo que implique uno de estos) se aplique también al mismo elemento. Si se usa cualquier atributo único, los otros dos se aplicarán automáticamente. Por ejemplo, si se aplica `progid`, también se aplican `vi_progid` y `coclass`.

## <a name="example"></a>Ejemplo

El código siguiente proporciona la sincronización para el método `UpdateBalance` del objeto `CMyClass`.

```cpp
// cpp_attr_ref_synchronize.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module(name="SYNC")];

[coclass,
threading(both),
vi_progid("MyProject.MyClass"),
progid("MyProject.MyClass.1"),
uuid("7a7baa0d-59b8-4576-b754-79d07e1d1cc3")
]
class CMyClass {
   float m_nBalance;

   [synchronize]
   void UpdateBalance(float nAdjust) {
      m_nBalance += nAdjust;
   }
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Método de clase, método|
|**Reiterativo**|No|
|**Atributos requeridos**|Uno o varios de los siguientes: `coclass`, `progid`o `vi_progid`.|
|**Atributos no válidos**|None|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos COM](com-attributes.md)
