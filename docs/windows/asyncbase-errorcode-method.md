---
title: Método Asyncbase | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::ErrorCode
dev_langs:
- C++
helpviewer_keywords:
- ErrorCode method
ms.assetid: 3f5f0f69-d60a-4a67-8cc6-a55fdc89a192
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8da9da0ffbfb8291082f7f600ca72bf1937c3bfc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435550"
---
# <a name="asyncbaseerrorcode-method"></a>AsyncBase::ErrorCode (Método)

Recupera el código de error para la operación asincrónica actual.

## <a name="syntax"></a>Sintaxis

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>Parámetros

*Error*<br/>
La ubicación donde esta operación almacena el código de error actual.

## <a name="remarks"></a>Comentarios

Esta operación es segura para subprocesos.

## <a name="requirements"></a>Requisitos

**Encabezado:** async.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[AsyncBase (clase)](../windows/asyncbase-class.md)