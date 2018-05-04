---
title: Enlaces de error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, failure hooks
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be598a77ca48eeee03360a3b598b0567abc6ee4b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="failure-hooks"></a>Enlaces de error
El enlace de error está habilitado en la misma manera que el [enlace de notificación](../../build/reference/notification-hooks.md). La rutina del enlace tiene que devolver un valor apropiado de modo que el proceso puede continuar (HINSTANCE o FARPROC) o 0 para indicar que se debe producir una excepción.  
  
 La variable de puntero que hace referencia a la función definida por el usuario es:  
  
```  
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}  
ExternC  
PfnDliHook   __pfnDliFailureHook2;  
```  
  
 El **DelayLoadInfo** estructura contiene todos los datos necesarios para generar informes precisos del error, incluido el valor de `GetLastError`.  
  
 Si la notificación es **dliFailLoadLib**, la función de enlace puede devolver:  
  
-   0, si no puede controlar el error.  
  
-   HMODULE, si el enlace de error corrige el problema y carga la propia biblioteca.  
  
 Si la notificación es **dliFailGetProc**, la función de enlace puede devolver:  
  
-   0, si no puede controlar el error.  
  
-   Una dirección de procedimiento válida (dirección de función de importación), si el enlace de error se realizó correctamente para la obtención de la propia dirección.  
  
## <a name="see-also"></a>Vea también  
 [Notificación y control de errores](../../build/reference/error-handling-and-notification.md)