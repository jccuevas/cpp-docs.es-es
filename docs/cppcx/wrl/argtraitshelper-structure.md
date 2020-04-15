---
title: ArgTraitsHelper (estructura)
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
- event/Microsoft::WRL::Details::ArgTraitsHelper::args
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraitsHelper structure
- Microsoft::WRL::Details::ArgTraitsHelper::args constant
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
ms.openlocfilehash: 4acbd9fa660f29bbaf209282ff0e90f43621574d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360778"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper (estructura)

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>Parámetros

*TDelegateInterface*<br/>
Una interfaz de delegado.

## <a name="remarks"></a>Observaciones

Ayuda a definir características comunes de argumentos delegados.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Nombre         | Descripción
------------ | ------------------------------------------------------
`methodType` | Sinónimo de `decltype(&TDelegateInterface::Invoke)`.
`Traits`     | Sinónimo de `ArgTraits<methodType>`.

### <a name="public-constants"></a>Constantes públicas

Nombre                           | Descripción
------------------------------ | ---------------------------------------------------------------------------------------------------------------------
[ArgTraitsHelper::args](#args) | Ayuda a [ArgTraits::args a](#args) mantener el `Invoke` recuento del número de parámetros en el método de una interfaz de delegado.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ArgTraitsHelper`

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Espacio de nombres:** Microsoft::WRL::Details

## <a name="argtraitshelperargs"></a><a name="args"></a>ArgTraitsHelper::args

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
static const int args = Traits::args;
```

### <a name="remarks"></a>Observaciones

Ayuda `ArgTraitsHelper::args` a mantener el recuento `Invoke` del número de parámetros en el método de una interfaz de delegado.
