---
title: sincronizar (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.synchronize
helpviewer_keywords:
- synchronize attribute
ms.assetid: 15fc8544-955d-4765-b3d5-0f619c8b3f40
ms.openlocfilehash: ea5236b887fb0df2a0acdd1e4050c66a4719072b
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037065"
---
# <a name="synchronize"></a>synchronize

Sincroniza el acceso al método de destino.

## <a name="syntax"></a>Sintaxis

```cpp
[synchronize]
```

## <a name="remarks"></a>Comentarios

El **sincronizar** atributo de C++ implementa la compatibilidad con el método de destino de un objeto de sincronización. La sincronización permite varios objetos usar un recurso común (por ejemplo, un método de una clase) controlando el acceso del método de destino.

El código insertado por este atributo llama adecuada `Lock` método (determinado por el modelo de subprocesos) al principio del método de destino. Cuando se sale del método, `Unlock` se llama automáticamente. Para obtener más información sobre estas funciones, vea [CComAutoThreadModule::Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)

Este atributo requiere que el atributo [coclass](coclass.md), [progid](progid.md)o [vi_progid](vi-progid.md) (u otro atributo que implique uno de estos) se aplique también al mismo elemento. Si se usa cualquier atributo único, los otros dos se aplicarán automáticamente. Por ejemplo, si `progid` se aplica, `vi_progid` y `coclass` también se aplican.

## <a name="example"></a>Ejemplo

El código siguiente proporciona sincronización para el `UpdateBalance` método de la `CMyClass` objeto.

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
|**Atributos requeridos**|Una o varias de las siguientes acciones: `coclass`, `progid`, o `vi_progid`.|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos COM](com-attributes.md)