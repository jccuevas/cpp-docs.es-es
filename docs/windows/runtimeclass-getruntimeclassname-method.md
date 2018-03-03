---
title: "Runtimeclass:: Getruntimeclassname (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetRuntimeClassName
dev_langs:
- C++
helpviewer_keywords:
- GetRuntimeClassName method
ms.assetid: f6388163-fe65-4948-a4bc-ae6826f480e7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9987c539bb67e3989af851c3e4088e25b67f9136
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="runtimeclassgetruntimeclassname-method"></a>RuntimeClass::GetRuntimeClassName (Método)

Obtiene el nombre de clase en tiempo de ejecución del objeto RuntimeClass actual.

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

Un error de aserción está si emitido &#95; &#95; WRL_STRICT &#95; &#95; o &#95; &#95; WRL_FORCE_INSPECTABLE_CLASS_MACRO &#95; &#95; no se ha definido.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[RuntimeClass (clase)](../windows/runtimeclass-class.md)