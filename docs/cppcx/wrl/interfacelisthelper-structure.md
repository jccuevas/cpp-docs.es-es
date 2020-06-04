---
title: InterfaceListHelper (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceListHelper
helpviewer_keywords:
- InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
ms.openlocfilehash: 1a7b4c19bbcdd4161e9078274f18f96a48f9e7d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213855"
---
# <a name="interfacelisthelper-structure"></a>InterfaceListHelper (estructura)

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

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

*To*<br/>
Parámetro de plantilla 0, que es obligatorio.

*T1*<br/>
Parámetro de plantilla 1, que, de forma predeterminada, no se especifica.

*T2*<br/>
Parámetro de plantilla 2, que, de forma predeterminada, no se especifica. El tercer parámetro de plantilla.

*T3*<br/>
Parámetro de plantilla 3, que, de forma predeterminada, no se especifica.

*T4*<br/>
Parámetro de plantilla 4, que, de forma predeterminada, no se especifica.

*T5*<br/>
Parámetro de plantilla 5, que, de forma predeterminada, no se especifica.

*T6*<br/>
Parámetro de plantilla 6, que, de forma predeterminada, no se especifica.

*T7*<br/>
Parámetro de plantilla 7, que, de forma predeterminada, no se especifica.

*T8*<br/>
Parámetro de plantilla 8, que, de forma predeterminada, no se especifica.

*T9*<br/>
Parámetro de plantilla 9, que, de forma predeterminada, no se especifica.

## <a name="remarks"></a>Observaciones

Compila un tipo de `InterfaceList` mediante la aplicación de los argumentos de parámetro de plantilla especificados de forma recursiva.

La plantilla **interfacelisthelper (** usa el parámetro de plantilla *T0* para definir el primer miembro de datos en una estructura de `InterfaceList` y, a continuación, aplica de forma recursiva la plantilla **interfacelisthelper (** a cualquier parámetro de plantilla restante. **Interfacelisthelper (** se detiene cuando no hay ningún parámetro de plantilla restante.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`TypeT`|Sinónimo del tipo Interfacelist (.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`InterfaceListHelper`

## <a name="requirements"></a>Requisitos

**Encabezado:** implementa. h

**Espacio de nombres:** Microsoft:: WRL::D etalles

## <a name="see-also"></a>Consulte también

[Microsoft::WRL::Details (espacio de nombres)](microsoft-wrl-details-namespace.md)
