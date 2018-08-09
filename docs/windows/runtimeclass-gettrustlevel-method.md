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
ms.openlocfilehash: adcec3f4a531a6c48e0995468994900124746e4b
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015136"
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