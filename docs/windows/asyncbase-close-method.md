---
title: Método Asyncbase | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: a52b1124-754b-4393-b491-64aae0c22f1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 732eb6f8668f7742e23e1ea410dcc659bc3d36c7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605351"
---
# <a name="asyncbaseclose-method"></a>AsyncBase::Close (Método)

Cierra la operación asincrónica.

## <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(
   Close
)(void) override;
```

## <a name="return-value"></a>Valor devuelto

S_OK si la operación cierra o ya está cerrado; en caso contrario, E_ILLEGAL_STATE_CHANGE.

## <a name="remarks"></a>Comentarios

**Close()** es una implementación predeterminada de `IAsyncInfo::Close`, y no se realiza ningún trabajo real. Para cerrar realmente una operación asincrónica, invalidar el `OnClose()` método virtual puro.

## <a name="requirements"></a>Requisitos

**Encabezado:** async.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[AsyncBase (clase)](../windows/asyncbase-class.md)