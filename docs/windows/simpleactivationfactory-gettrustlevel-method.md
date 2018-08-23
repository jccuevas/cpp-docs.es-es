---
title: Método Simpleactivationfactory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
dev_langs:
- C++
ms.assetid: 99aa9bc9-d954-4a6f-902b-4abe00e43039
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b5a1838c153dc7a0a4def9f98e5e043e36ae9414
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603850"
---
# <a name="simpleactivationfactorygettrustlevel-method"></a>SimpleActivationFactory::GetTrustLevel (Método)

Obtiene el nivel de confianza de una instancia de la clase especificada por el `Base` parámetro de plantilla de clase.

## <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>Parámetros

*trustLvl*  
Cuando se completa esta operación, el nivel de confianza del objeto de clase actual.

## <a name="return-value"></a>Valor devuelto

Siempre S_OK.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[SimpleActivationFactory (clase)](../windows/simpleactivationfactory-class.md)