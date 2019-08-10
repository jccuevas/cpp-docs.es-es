---
title: Excepciones (C/C++)
ms.date: 11/04/2016
f1_keywords:
- ERROR_MOD_NOT_FOUND
- vcppException
- ERROR_SEVERITY_ERROR
helpviewer_keywords:
- vcppException
- C++ exception handling, delayed loading of DLLs
- delayed loading of DLLs, exceptions
- ERROR_SEVERITY_ERROR exception
- ERROR_MOD_NOT_FOUND exception
ms.assetid: c03be05d-1c39-4f35-84cf-00c9af3bae9a
ms.openlocfilehash: cf38af464f08e143ed9073befe30f6aeb8b913b6
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915457"
---
# <a name="exceptions-cc"></a>Excepciones (C/C++)

Se pueden producir dos códigos de excepción cuando se detectan errores:

- Para un error de **LoadLibrary**

- Para un error de **GetProcAddress**

Esta es la información de la excepción:

```
//
// Exception information
//
#define FACILITY_VISUALCPP  ((LONG)0x6d)
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)
```

Los códigos de excepción que se inician son los valores estándar de VcppException (ERROR_SEVERITY_ERROR, ERROR_MOD_NOT_FOUND) y VcppException (ERROR_SEVERITY_ERROR, ERROR_PROC_NOT_FOUND). La excepción pasa un puntero a una estructura **DelayLoadInfo** en el valor LPDWORD que se puede recuperar mediante **GetExceptionInformation** en el campo [EXCEPTION_RECORD](/windows/desktop/api/winnt/ns-winnt-exception_record) Structure, ExceptionInformation [0].

Además, si se establecen bits incorrectos en el campo grAttrs, se produce la excepción ERROR_INVALID_PARAMETER. Esta excepción es, para todas las intenciones y propósitos, fatal.

Consulte [definiciones de estructura y constante](structure-and-constant-definitions.md) para obtener más información.

## <a name="see-also"></a>Vea también

[Notificación y control de errores](error-handling-and-notification.md)
