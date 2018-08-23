---
title: Continueasyncoperation (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
dev_langs:
- C++
helpviewer_keywords:
- ContinueAsyncOperation method
ms.assetid: ce38181d-2fc3-4579-b0ce-237a3c7648bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b83d7a0bb5eadede42d2572d5ebc5a02a0fe9a0e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607190"
---
# <a name="asyncbasecontinueasyncoperation-method"></a>AsyncBase::ContinueAsyncOperation (Método)

Determina si la operación asincrónica, debe continuar el procesamiento o debería detenerse.

## <a name="syntax"></a>Sintaxis

```cpp
inline bool ContinueAsyncOperation();
```

## <a name="return-value"></a>Valor devuelto

**True** si el estado actual de la operación asincrónica es *iniciado*, lo que significa que la operación debe continuar. En caso contrario, **false**, lo que significa que la operación debe detenerse.

## <a name="requirements"></a>Requisitos

**Encabezado:** async.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[AsyncBase (clase)](../windows/asyncbase-class.md)