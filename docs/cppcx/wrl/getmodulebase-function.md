---
title: GetModuleBase (Función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
ms.openlocfilehash: 0d130fffa9fad9ae327d03eaa01d84742094cc67
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213972"
---
# <a name="getmodulebase-function"></a>GetModuleBase (Función)

Recupera un puntero [ModuleBase](modulebase-class.md) que permite aumentar y reducir el recuento de referencias de un objeto [RuntimeClass](runtimeclass-class.md) .

## <a name="syntax"></a>Sintaxis

```cpp
inline Details::ModuleBase* GetModuleBase() throw()
```

## <a name="return-value"></a>Valor devuelto

Puntero a un objeto `ModuleBase` .

## <a name="remarks"></a>Observaciones

Esta función se usa internamente para aumentar y disminuir los recuentos de referencias de objetos.

Puede usar esta función para controlar los recuentos de referencias mediante una llamada a [ModuleBase:: incrementobjectcount (](modulebase-class.md#incrementobjectcount) y [ModuleBase::D ecrementobjectcount](modulebase-class.md#decrementobjectcount).

## <a name="requirements"></a>Requisitos

**Encabezado:** implementa. h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Consulte también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)
