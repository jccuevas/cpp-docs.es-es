---
title: 'Runtimeclass:: Gettrustlevel (método) | Documentos de Microsoft'
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
ms.openlocfilehash: bc588950cc8752a7c2b8e1ddf00b2193aaf0f395
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="runtimeclassgettrustlevel-method"></a>RuntimeClass::GetTrustLevel (Método)

Obtiene el nivel de confianza del objeto RuntimeClass actual.

## <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>Parámetros

*trustLvl*  
Cuando se completa esta operación, el nivel de confianza del objeto RuntimeClass actual.

## <a name="return-value"></a>Valor devuelto

Siempre S_OK.

## <a name="remarks"></a>Comentarios

Se genera un error de aserción si &#95; &#95;WRL_STRICT&#95; &#95; o &#95; &#95;WRL_FORCE_INSPECTABLE_CLASS_MACRO&#95; &#95; no está definido.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[RuntimeClass (clase)](../windows/runtimeclass-class.md)