---
title: GetModuleBase (Función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
ms.openlocfilehash: 40289903eba2ce7ac35d4d0b208c3b609efb09f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650819"
---
# <a name="getmodulebase-function"></a>GetModuleBase (Función)
Recupera un [ModuleBase](../windows/modulebase-class.md) puntero que permite aumentar y disminuir el recuento de referencias de un [RuntimeClass](../windows/runtimeclass-class.md) objeto.

## <a name="syntax"></a>Sintaxis

```cpp
inline Details::ModuleBase* GetModuleBase() throw()
```

## <a name="return-value"></a>Valor devuelto

Puntero a un objeto `ModuleBase` .

## <a name="remarks"></a>Comentarios

Esta función se usa internamente para incrementar y disminuir recuentos de referencias de objeto.

Puede usar esta función para controlar los recuentos de referencia mediante una llamada a [Modulebase](../windows/modulebase-incrementobjectcount-method.md) y [Modulebase](../windows/modulebase-decrementobjectcount-method.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)