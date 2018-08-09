---
title: Getruntimeclassname (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetRuntimeClassName
dev_langs:
- C++
helpviewer_keywords:
- GetRuntimeClassName method
ms.assetid: f6388163-fe65-4948-a4bc-ae6826f480e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 126133c5e542414f1fb38635e1cb14314bc55d52
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020400"
---
# <a name="runtimeclassgetruntimeclassname-method"></a>RuntimeClass::GetRuntimeClassName (Método)

Obtiene el nombre de clase en tiempo de ejecución del elemento actual **RuntimeClass** objeto.

## <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>Parámetros
*runtimeName*  
Cuando se completa esta operación, el nombre de clase en tiempo de ejecución.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="remarks"></a>Comentarios

Se genera un error de aserción si `__WRL_STRICT__` o `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` no está definido.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también
 [RuntimeClass (clase)](../windows/runtimeclass-class.md)