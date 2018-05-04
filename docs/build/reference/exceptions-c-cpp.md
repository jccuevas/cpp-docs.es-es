---
title: Excepciones (C/C ++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- ERROR_MOD_NOT_FOUND
- vcppException
- ERROR_SEVERITY_ERROR
dev_langs:
- C++
helpviewer_keywords:
- vcppException
- C++ exception handling, delayed loading of DLLs
- delayed loading of DLLs, exceptions
- ERROR_SEVERITY_ERROR exception
- ERROR_MOD_NOT_FOUND exception
ms.assetid: c03be05d-1c39-4f35-84cf-00c9af3bae9a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 819f9424b2439cc49517afe54d62a8ed4f06d22d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="exceptions-cc"></a>Excepciones (C/C++)
Cuando se encuentran errores, se pueden generar dos códigos de excepción:  
  
-   Para una **LoadLibrary** error  
  
-   Para una **GetProcAddress** error  
  
 Esta es la información de excepción:  
  
```  
//  
// Exception information  
//  
#define FACILITY_VISUALCPP  ((LONG)0x6d)  
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)  
```  
  
 Los códigos de excepción que produce son el estándar VcppException (ERROR_SEVERITY_ERROR, ERROR_MOD_NOT_FOUND) y los valores de VcppException (ERROR_SEVERITY_ERROR, ERROR_PROC_NOT_FOUND). La excepción pasa un puntero a un **DelayLoadInfo** estructura en el valor LPDWORD que se puede recuperar **GetExceptionInformation** en el [EXCEPTION_RECORD](http://msdn.microsoft.com/library/windows/desktop/aa363082) estructura, campo ExceptionInformation [0].  
  
 Además, si los bits incorrectos se establecen en el campo grAttrs son, se produce la excepción ERROR_INVALID_PARAMETER. Esta excepción es, por todos los propósitos, irrecuperable.  
  
 Vea [definiciones de estructura y constante](../../build/reference/structure-and-constant-definitions.md) para obtener más información.  
  
## <a name="see-also"></a>Vea también  
 [Notificación y control de errores](../../build/reference/error-handling-and-notification.md)