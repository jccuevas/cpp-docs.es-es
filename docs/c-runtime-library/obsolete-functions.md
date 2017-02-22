---
title: "Funciones obsoletas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_wctype"
  - "_loaddll"
  - "_unloaddll"
  - "_getdllprocaddr"
  - "_seterrormode"
  - "_beep"
  - "_sleep"
  - "_getsystime"
  - "corecrt_wctype/is_wctype"
  - "process/_loaddll"
  - "process/_unloaddll"
  - "process/_getdllprocaddr"
  - "stdlib/_seterrormode"
  - "stdlib/_beep"
  - "stdlib/_sleep"
  - "time/_getsystime"
  - "time/_setsystime"
dev_langs: 
  - "C++"
ms.assetid: 8e14c2d4-1481-4240-8586-47eb43db02b0
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Funciones obsoletas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Algunas funciones de biblioteca son obsoletas y tienen equivalentes más recientes. Se recomienda que las cambie a las versiones actualizadas. Otras funciones obsoletas se han quitado de CRT. En este tema se muestran las funciones desusadas como obsoletas y las funciones quitadas de una versión concreta de Visual Studio.  
  
## En desuso como obsoleta en Visual Studio 2015  
  
|Función obsoleta|Alternativa|  
|----------------------|-----------------|  
|`is_wctype`|[iswctype](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|  
|`_loaddll`|[LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187), [LoadLibraryEx](http://go.microsoft.com/fwlink/p/?LinkID=236091) o [LoadPackagedLibrary](https://msdn.microsoft.com/library/windows/desktop/hh447159\(v=vs.85\).aspx)|  
|`_unloaddll`|[FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188)|  
|`_getdllprocaddr`|[GetProcAddress](../build/getprocaddress.md)|  
|`_seterrormode`|[SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkID=255242)|  
|`_beep`|[Beep](https://msdn.microsoft.com/library/windows/desktop/ms679277\(v=vs.85\).aspx)|  
|`_sleep`|[Sleep](https://msdn.microsoft.com/library/windows/desktop/ms686298\(v=vs.85\).aspx)|  
|`_getsystime`|[GetLocalTime](https://msdn.microsoft.com/library/windows/desktop/ms724338\(v=vs.85\).aspx)|  
|`_setsystime`|[SetLocalTime](https://msdn.microsoft.com/library/windows/desktop/ms724936\(v=vs.85\).aspx)|  
  
## Se ha quitado de CRT en Visual Studio 2015  
  
|Función obsoleta|Alternativa|  
|----------------------|-----------------|  
|[\_cgets, \_cgetws](../c-runtime-library/cgets-cgetws.md)|[\_cgets\_s, \_cgetws\_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|  
|[gets, \_getws](../c-runtime-library/gets-getws.md)|[gets\_s, \_getws\_s](../c-runtime-library/reference/gets-s-getws-s.md)|  
|[\_get\_output\_format](../c-runtime-library/get-output-format.md)|Ninguno|  
|[\_heapadd](../c-runtime-library/heapadd.md)|Ninguna|  
|[\_heapset](../c-runtime-library/heapset.md)|Ninguna|  
|[inp, inpw](../c-runtime-library/inp-inpw.md)|Ninguna|  
|[\_inp, \_inpw, \_inpd](../c-runtime-library/inp-inpw-inpd.md)|Ninguna|  
|[outp, outpw](../c-runtime-library/outp-outpw.md)|Ninguna|  
|[\_outp, \_outpw, \_outpd](../c-runtime-library/outp-outpw-outpd.md)|Ninguna|  
|[\_set\_output\_format](../c-runtime-library/set-output-format.md)|Ninguno|  
  
## Se ha quitado de CRT en versiones anteriores de Visual Studio  
 [\_lock](../c-runtime-library/lock.md)  
  
 [\_unlock](../c-runtime-library/unlock.md)