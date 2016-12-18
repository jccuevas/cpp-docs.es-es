---
title: "Enlaces de error | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "carga retrasada de archivos DLL, enlaces de error"
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Enlaces de error
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El enlace de error se habilita del mismo modo que el [enlace de notificación](../../build/reference/notification-hooks.md).  La rutina del enlace tiene que devolver un valor apropiado para que pueda continuar el procesamiento \(HINSTANCE o FARPROC\) o el valor 0 para indicar que debe producirse una excepción.  
  
 La variable de puntero que hace referencia a la función definida por el usuario es:  
  
```  
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}  
ExternC  
PfnDliHook   __pfnDliFailureHook2;  
```  
  
 La estructura **DelayLoadInfo** contiene todos los datos necesarios para ofrecer un informe preciso del error, incluyendo el valor de `GetLastError`.  
  
 Si la notificación es **dliFailLoadLib**, la función de enlace puede devolver:  
  
-   0, si no puede controlar el error.  
  
-   HMODULE, si el enlace de error corrige el problema y carga la propia biblioteca.  
  
 Si la notificación es **dliFailGetProc**, la función de enlace puede devolver:  
  
-   0, si no puede controlar el error.  
  
-   Una dirección de procedimiento válida \(dirección de funciones de importación\), si el enlace de error obtiene correctamente la propia dirección.  
  
## Vea también  
 [Notificación y control de errores](../../build/reference/error-handling-and-notification.md)