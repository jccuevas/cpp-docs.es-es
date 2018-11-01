---
title: InterfaceListHelper (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceListHelper
helpviewer_keywords:
- InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
ms.openlocfilehash: ae9bf9d9c1301c142f94cb23cf6b0c2774f79bb4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464784"
---
# <a name="interfacelisthelper-structure"></a>InterfaceListHelper (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <
    typename T0,
    typename T1 = Nil,
    typename T2 = Nil,
    typename T3 = Nil,
    typename T4 = Nil,
    typename T5 = Nil,
    typename T6 = Nil,
    typename T7 = Nil,
    typename T8 = Nil,
    typename T9 = Nil
>
struct InterfaceListHelper;

template <typename T0>
struct InterfaceListHelper<T0, Nil, Nil, Nil, Nil, Nil, Nil, Nil, Nil>;
```

### <a name="parameters"></a>Parámetros

*T0*<br/>
Parámetro de plantilla 0, que es necesario.

*T1*<br/>
Parámetro de plantilla 1, que no se especifica de forma predeterminada.

*T2*<br/>
Parámetro de plantilla 2, que no se especifica de forma predeterminada. El tercer parámetro de plantilla.

*T3*<br/>
Parámetro de plantilla 3, que no se especifica de forma predeterminada.

*T4*<br/>
Parámetro de plantilla 4, que no se especifica de forma predeterminada.

*T5*<br/>
Parámetro de plantilla 5, que no se especifica de forma predeterminada.

*T6*<br/>
Parámetro de plantilla 6, que no se especifica de forma predeterminada.

*T7*<br/>
Parámetro de plantilla 7, que no se especifica de forma predeterminada.

*T8*<br/>
Parámetro de plantilla 8, que no se especifica de forma predeterminada.

*T9*<br/>
Parámetro de plantilla 9, que no se especifica de forma predeterminada.

## <a name="remarks"></a>Comentarios

Compila una `InterfaceList` tipo mediante la aplicación de los argumentos de parámetro de plantilla especificado recursiva.

El **InterfaceListHelper** plantilla usa el parámetro de plantilla *T0* para definir el primer miembro de datos en un `InterfaceList` estructura y, a continuación, de forma recursiva se aplica el  **InterfaceListHelper** plantilla los parámetros de plantilla restantes. **InterfaceListHelper** se detiene cuando no hay ningún parámetro de plantilla restantes.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`TypeT`|Un sinónimo del tipo InterfaceList.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`InterfaceListHelper`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)