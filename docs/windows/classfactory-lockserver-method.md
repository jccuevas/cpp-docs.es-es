---
title: Lockserver (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::LockServer
dev_langs:
- C++
helpviewer_keywords:
- LockServer method
ms.assetid: 8d859815-956d-4f81-a5af-7cdee7e945de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5ea76974359da2002178a342ab7d9b5523c52889
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584143"
---
# <a name="classfactorylockserver-method"></a>ClassFactory::LockServer (Método)

Incrementa o disminuye el número de subyacentes de objetos que se realiza el seguimiento actual **ClassFactory** objeto.

## <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>Parámetros

*manada*  
**True** para incrementar el número de objetos con seguimiento. **false** para reducir el número de objetos con seguimiento.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, E_FAIL.

## <a name="remarks"></a>Comentarios

**ClassFactory** realiza un seguimiento de los objetos en una instancia subyacente de la [módulo](../windows/module-class.md) clase.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[ClassFactory (clase)](../windows/classfactory-class.md)