---
title: Firecompletion (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::FireCompletion
dev_langs:
- C++
helpviewer_keywords:
- FireCompletion method
ms.assetid: b5e29d6d-52e7-4148-a7f3-a313b1359819
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19b796b1fbc618bb909b186aa86d3c893c8536c5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600261"
---
# <a name="asyncbasefirecompletion-method"></a>AsyncBase::FireCompletion (Método)

Invoca el controlador de eventos de finalización o restablece al delegado de progreso interno.

## <a name="syntax"></a>Sintaxis

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

## <a name="remarks"></a>Comentarios

La primera versión de **FireCompletion()** restablece la variable de delegado de progreso interno. La segunda versión invoca el controlador de eventos de finalización si se ha completado la operación asincrónica.

## <a name="requirements"></a>Requisitos

**Encabezado:** async.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[AsyncBase (clase)](../windows/asyncbase-class.md)