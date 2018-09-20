---
title: Método Asyncbase | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_Id
dev_langs:
- C++
helpviewer_keywords:
- get_Id method
ms.assetid: 591d8366-ea76-4deb-9278-9d3bc394a42b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ee4e15293d3f1f7b5b364ea22eeea2385cc9e855
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403882"
---
# <a name="asyncbasegetid-method"></a>AsyncBase::get_Id (Método)

Recupera el identificador de la operación asincrónica.

## <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>Parámetros

*identificador*<br/>
La ubicación donde se almacenará el identificador.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, E_ILLEGAL_METHOD_CALL.

## <a name="remarks"></a>Comentarios

Este método implementa `IAsyncInfo::get_Id`.

## <a name="requirements"></a>Requisitos

**Encabezado:** async.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[AsyncBase (clase)](../windows/asyncbase-class.md)