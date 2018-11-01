---
title: RaiseException (función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
ms.openlocfilehash: af0b35e1014f79c7907711b95200c241d31b6117
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594758"
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

*recursos humanos*<br/>
El código de excepción de la excepción; es decir, el valor HRESULT de una operación con errores.

*dwExceptionFlags*<br/>
Una marca que indica una excepción crítico (el valor de la marca es cero), o una excepción noncontinuable (el valor de la marca es distinto de cero). De forma predeterminada, la excepción es que no dejaba continuar.

## <a name="remarks"></a>Comentarios

Genera una excepción en el subproceso de llamada.

Para obtener más información, consulte el Windows `RaiseException` función.

## <a name="requirements"></a>Requisitos

**Encabezado:** internal.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)