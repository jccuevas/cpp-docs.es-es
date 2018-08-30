---
title: Excepciones (C/C ++) | Microsoft Docs
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
ms.openlocfilehash: 40a3a9e1cf1384603d6b7d95fa5960e951f932ef
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216888"
---
# <a name="exceptions-cc"></a>Excepciones (C/C++)
Cuando se producen errores, se pueden generar dos códigos de excepción:  
  
-   Para un **LoadLibrary** error  
  
-   Para un **GetProcAddress** error  
  
 Esta es la información de excepción:  
  
```  
//  
// Exception information  
//  
#define FACILITY_VISUALCPP  ((LONG)0x6d)  
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)  
```  
  
 Los códigos de excepción que produce son las estándar VcppException (ERROR_SEVERITY_ERROR, ERROR_MOD_NOT_FOUND) y los valores de VcppException (ERROR_SEVERITY_ERROR, ERROR_PROC_NOT_FOUND). La excepción pasa un puntero a un **DelayLoadInfo** estructura en el valor LPDWORD que se puede recuperar **GetExceptionInformation** en el [EXCEPTION_RECORD](/windows/desktop/api/winnt/ns-winnt-_exception_record) estructura, campo ExceptionInformation [0].  
  
 Además, si los bits incorrectos se establecen en el campo grAttrs son, se produce la excepción ERROR_INVALID_PARAMETER. Esta excepción es, por todos los propósitos, grave.  
  
 Consulte [definiciones de estructura y constante](../../build/reference/structure-and-constant-definitions.md) para obtener más información.  
  
## <a name="see-also"></a>Vea también  
 [Notificación y control de errores](../../build/reference/error-handling-and-notification.md)