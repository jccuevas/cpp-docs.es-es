---
title: RaiseException (función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
ms.openlocfilehash: 08305c5d59d7e272aac87ad9aa183c8e82588632
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62231358"
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

*hr*<br/>
El código de excepción de la excepción; es decir, el valor HRESULT de una operación con errores.

*dwExceptionFlags*<br/>
Una marca que indica una excepción crítico (el valor de la marca es cero), o una excepción noncontinuable (el valor de la marca es distinto de cero). De forma predeterminada, la excepción es que no dejaba continuar.

## <a name="remarks"></a>Comentarios

Genera una excepción en el subproceso de llamada.

Para obtener más información, consulte el Windows `RaiseException` función.

## <a name="requirements"></a>Requisitos

**Encabezado:** internal.h

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](microsoft-wrl-details-namespace.md)