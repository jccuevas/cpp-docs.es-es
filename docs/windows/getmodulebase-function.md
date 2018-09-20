---
title: GetModuleBase (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
dev_langs:
- C++
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4d460b006d2d17df308a62c0433621aac7008f4d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411422"
---
# <a name="getmodulebase-function"></a>GetModuleBase (Función)
Recupera un [ModuleBase](../windows/modulebase-class.md) puntero que permite aumentar y disminuir el recuento de referencias de un [RuntimeClass](../windows/runtimeclass-class.md) objeto.
  
## <a name="syntax"></a>Sintaxis
  
```cpp
inline Details::ModuleBase* GetModuleBase() throw()  
```
  
## <a name="return-value"></a>Valor devuelto

Un puntero a un `ModuleBase` objeto.
  
## <a name="remarks"></a>Comentarios

Esta función se usa internamente para incrementar y disminuir recuentos de referencias de objeto.
  
Puede usar esta función para controlar los recuentos de referencia mediante una llamada a [Modulebase](../windows/modulebase-incrementobjectcount-method.md) y [Modulebase](../windows/modulebase-decrementobjectcount-method.md).
  
## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h
  
**Espacio de nombres:** Microsoft::WRL
  
## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)