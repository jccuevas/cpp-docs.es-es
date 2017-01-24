---
title: "Excepciones (C/C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ERROR_MOD_NOT_FOUND"
  - "vcppException"
  - "ERROR_SEVERITY_ERROR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de excepciones de C++, carga retrasada de archivos DLL"
  - "carga retrasada de archivos DLL, excepciones"
  - "ERROR_MOD_NOT_FOUND (excepción)"
  - "ERROR_SEVERITY_ERROR (excepción)"
  - "vcppException"
ms.assetid: c03be05d-1c39-4f35-84cf-00c9af3bae9a
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Excepciones (C/C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Hay dos códigos de excepción que se pueden producir cuando se encuentran errores:  
  
-   Para un error de **LoadLibrary**  
  
-   Para un error de **GetProcAddress**  
  
 Esta es la información de excepción:  
  
```  
//  
// Exception information  
//  
#define FACILITY_VISUALCPP  ((LONG)0x6d)  
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)  
```  
  
 Los códigos de error producidos son los valores de VcppException\(ERROR\_SEVERITY\_ERROR, ERROR\_MOD\_NOT\_FOUND\) y VcppException\(ERROR\_SEVERITY\_ERROR, ERROR\_PROC\_NOT\_FOUND\) estándar.  La excepción pasa un puntero a una estructura **DelayLoadInfo** en el valor LPDWORD que se puede recuperar mediante **GetExceptionInformation** en la estructura [EXCEPTION\_RECORD](http://msdn.microsoft.com/library/windows/desktop/aa363082), campo ExceptionInformation\[0\].  
  
 Además, si los bits que se establecen en el campo grAttrs son incorrectos, se produce la excepción ERROR\_INVALID\_PARAMETER.  Esta excepción es grave en cualquier caso.  
  
 Vea [Definiciones de estructura y de constante](../../build/reference/structure-and-constant-definitions.md) para obtener más información.  
  
## Vea también  
 [Notificación y control de errores](../../build/reference/error-handling-and-notification.md)