---
title: Gettrustlevel (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetTrustLevel
dev_langs:
- C++
helpviewer_keywords:
- GetTrustLevel method
ms.assetid: bd90407e-6dd7-41c3-9ea0-c402c276014a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c714f37a53e111c90333352610fd73532ac86fe7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599837"
---
# <a name="runtimeclassgettrustlevel-method"></a>RuntimeClass::GetTrustLevel (Método)

Obtiene el nivel de confianza del actual **RuntimeClass** objeto.

## <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>Parámetros

*trustLvl*  
Cuando finalice esta operación, el nivel de confianza del actual **RuntimeClass** objeto.

## <a name="return-value"></a>Valor devuelto

Siempre S_OK.

## <a name="remarks"></a>Comentarios

Se genera un error de aserción si `__WRL_STRICT__` o `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` no está definido.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[RuntimeClass (clase)](../windows/runtimeclass-class.md)