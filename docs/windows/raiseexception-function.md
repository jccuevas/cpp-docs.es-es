---
title: RaiseException (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
dev_langs:
- C++
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 49024e903237160cc26a9c095cf9f313b43ccb6f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600770"
---
# <a name="raiseexception-function"></a>RaiseException (función)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
inline void __declspec(noreturn)   RaiseException(
      HRESULT hr,
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);
```

### <a name="parameters"></a>Parámetros

*recursos humanos*  
El código de excepción de la excepción; es decir, el valor HRESULT de una operación con errores.

*dwExceptionFlags*  
Una marca que indica una excepción crítico (el valor de la marca es cero), o una excepción noncontinuable (el valor de la marca es distinto de cero). De forma predeterminada, la excepción es que no dejaba continuar.

## <a name="remarks"></a>Comentarios

Genera una excepción en el subproceso de llamada.

Para obtener más información, consulte el Windows `RaiseException` función.

## <a name="requirements"></a>Requisitos

**Encabezado:** internal.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)