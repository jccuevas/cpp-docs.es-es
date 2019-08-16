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
ms.openlocfilehash: 360acba73278902cc40d10fd975011488742a7a2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492929"
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

Los códigos de excepción que se inician son los valores estándar de VcppException (ERROR_SEVERITY_ERROR, ERROR_MOD_NOT_FOUND) y VcppException (ERROR_SEVERITY_ERROR, ERROR_PROC_NOT_FOUND). La excepción pasa un puntero a una estructura **DelayLoadInfo** en el valor LPDWORD que se puede recuperar mediante **GetExceptionInformation** en el campo [EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record) Structure, ExceptionInformation [0].

Además, si se establecen bits incorrectos en el campo grAttrs, se produce la excepción ERROR_INVALID_PARAMETER. Esta excepción es, para todas las intenciones y propósitos, fatal.

Consulte [definiciones de estructura y constante](structure-and-constant-definitions.md) para obtener más información.

## <a name="see-also"></a>Vea también

[Notificación y control de errores](error-handling-and-notification.md)
