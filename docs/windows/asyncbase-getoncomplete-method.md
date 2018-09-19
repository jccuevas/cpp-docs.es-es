---
title: Getoncomplete (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::GetOnComplete
dev_langs:
- C++
helpviewer_keywords:
- GetOnComplete method
ms.assetid: f06ae02d-9a88-41d2-b749-bdc1a7ff8748
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f9e6ee8da9c30ca3d5da9f772e46beca76f424be
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398448"
---
# <a name="asyncbasegetoncomplete-method"></a>AsyncBase::GetOnComplete (Método)

Copia la dirección del controlador de eventos de finalización actual a la variable especificada.

## <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>Parámetros

*completeHandler*<br/>
La ubicación donde se almacena la dirección del controlador de eventos de finalización actual.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, E_ILLEGAL_METHOD_CALL.

## <a name="requirements"></a>Requisitos

**Encabezado:** async.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[AsyncBase (clase)](../windows/asyncbase-class.md)