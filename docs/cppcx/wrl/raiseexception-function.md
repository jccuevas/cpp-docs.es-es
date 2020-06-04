---
title: RaiseException (función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
ms.openlocfilehash: 3270057bf5b1b27a98bef1ab236291eab15d27ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213634"
---
# <a name="raiseexception-function"></a>RaiseException (función)

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
inline void __declspec(noreturn)   RaiseException(
      HRESULT hr,
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);
```

### <a name="parameters"></a>Parámetros

*hora*<br/>
Código de excepción de la excepción que se está generando; es decir, el valor HRESULT de una operación con errores.

*dwExceptionFlags*<br/>
Marca que indica una excepción continua (el valor de la marca es cero) o una excepción no continua (el valor de la marca es distinto de cero). De forma predeterminada, la excepción no es continuable.

## <a name="remarks"></a>Observaciones

Genera una excepción en el subproceso que realiza la llamada.

Para obtener más información, vea la función `RaiseException` de Windows.

## <a name="requirements"></a>Requisitos

**Encabezado:** Internal. h

**Espacio de nombres:** Microsoft:: WRL::D etalles

## <a name="see-also"></a>Consulte también

[Microsoft::WRL::Details (espacio de nombres)](microsoft-wrl-details-namespace.md)
