---
title: AgileActivationFactory (Clase)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::AgileActivationFactory
ms.assetid: fab98f32-bb93-4c0f-badb-49fbddb194b0
ms.openlocfilehash: 854f998e31cfec577fb6ff0fb3d82dc1499f88bd
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59030652"
---
# <a name="agileactivationfactory-class"></a>AgileActivationFactory (Clase)

Representa un generador de activación de apartamento sencillo que implementa [FtmBase](ftmbase-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil,
    FactoryCacheFlags cacheFlagValue = FactoryCacheDefault
>
class AgileActivationFactory :
    public ActivationFactory<
        Implements<FtmBase, I0>,
        I1,
        I2,
        cacheFlagValue
    >;
```

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres**: Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)<br/>
[ActivationFactory (clase)](activationfactory-class.md)