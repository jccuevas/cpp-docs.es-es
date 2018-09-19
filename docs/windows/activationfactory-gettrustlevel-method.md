---
title: Método Activationfactory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::GetTrustLevel
dev_langs:
- C++
helpviewer_keywords:
- GetTrustLevel method
ms.assetid: 31547ae6-d2ab-4039-923c-154d53fb1a8b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bfec8bfa6940fd4a702334f0d3068c6d936ea8c1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607319"
---
# <a name="activationfactorygettrustlevel-method"></a>ActivationFactory::GetTrustLevel (Método)

Obtiene el nivel de confianza del objeto que actual **ActivationFactory** crea una instancia.

## <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>Parámetros

*trustLvl*  
Cuando se complete esta operación, el nivel de confianza de tiempo de ejecución de la clase que la **ActivationFactory** crea una instancia.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, se genera un error de aserción y *trustLvl* está establecido en `FullTrust`.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[ActivationFactory (clase)](../windows/activationfactory-class.md)