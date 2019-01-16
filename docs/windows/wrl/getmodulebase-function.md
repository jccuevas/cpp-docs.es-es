---
title: GetModuleBase (Función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
ms.openlocfilehash: 4d8c8467b7aeb9c21bf5f4ee19c60e6e60880688
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337541"
---
# <a name="getmodulebase-function"></a>GetModuleBase (función)

Recupera un [ModuleBase](modulebase-class.md) puntero que permite aumentar y disminuir el recuento de referencias de un [RuntimeClass](runtimeclass-class.md) objeto.

## <a name="syntax"></a>Sintaxis

```cpp
inline Details::ModuleBase* GetModuleBase() throw()
```

## <a name="return-value"></a>Valor devuelto

Puntero a un objeto `ModuleBase` .

## <a name="remarks"></a>Comentarios

Esta función se usa internamente para incrementar y disminuir recuentos de referencias de objeto.

Puede usar esta función para controlar los recuentos de referencia mediante una llamada a [Modulebase](modulebase-class.md#incrementobjectcount) y [Modulebase](modulebase-class.md#decrementobjectcount).

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres**: Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)