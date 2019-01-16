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
ms.openlocfilehash: fbba6d96106cc95910ccd9d0029cb3e9c254d7d3
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337686"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>Parámetros

*TDelegateInterface*<br/>
Una interfaz de delegado.

## <a name="remarks"></a>Comentarios

Ayuda a define las características comunes de los argumentos de delegado.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Name         | Descripción
------------ | ------------------------------------------------------
`methodType` | Sinónimo de `decltype(&TDelegateInterface::Invoke)`.
`Traits`     | Sinónimo de `ArgTraits<methodType>`.

### <a name="public-constants"></a>Constantes públicas

nombre                           | Descripción
------------------------------ | ---------------------------------------------------------------------------------------------------------------------
[ArgTraitsHelper::args](#args) | Ayuda a [Argtraits](#args) mantener el recuento del número de parámetros en el `Invoke` al método de interfaz de un delegado.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ArgTraitsHelper`

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="args"></a>ArgTraitsHelper::args

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
static const int args = Traits::args;
```

### <a name="remarks"></a>Comentarios

Ayuda a `ArgTraitsHelper::args` mantener el recuento del número de parámetros en el `Invoke` al método de interfaz de un delegado.
