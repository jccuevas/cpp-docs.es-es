---
title: Putoncomplete (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::PutOnComplete
dev_langs:
- C++
helpviewer_keywords:
- PutOnComplete method
ms.assetid: 1c469ff9-b2df-4637-bf05-01a617043149
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c62119b87183fe6a60c0ed4d987cbd12788d8a0d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602691"
---
# <a name="asyncbaseputoncomplete-method"></a>AsyncBase::PutOnComplete (Método)

Establece la dirección del controlador de eventos de finalización en el valor especificado.

## <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>Parámetros

*completeHandler*  
La dirección a la que se establece el controlador de eventos de finalización.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, E_ILLEGAL_METHOD_CALL.

## <a name="requirements"></a>Requisitos

**Encabezado:** async.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[AsyncBase (clase)](../windows/asyncbase-class.md)