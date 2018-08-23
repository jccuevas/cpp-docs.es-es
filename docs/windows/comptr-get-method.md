---
title: Método Comptr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::Get
dev_langs:
- C++
helpviewer_keywords:
- Get method
ms.assetid: 078eee51-7bca-4924-a74b-cd4f6a05de31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ca996b7893fd19076504fd91bbb5e80bbe692883
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42608669"
---
# <a name="comptrget-method"></a>ComPtr::Get (Método)

Recupera un puntero a la interfaz que está asociado a este **ComPtr**.

## <a name="syntax"></a>Sintaxis

```cpp
T* Get() const;
```

## <a name="return-value"></a>Valor devuelto

Puntero a la interfaz que está asociada a este **ComPtr**.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[ComPtr (clase)](../windows/comptr-class.md)