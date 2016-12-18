---
title: "_chdrive | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_chdrive"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "chdrive"
  - "_chdrive"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_chdrive (función)"
  - "chdrive (función)"
  - "unidades, cambiar"
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _chdrive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cambia la unidad de trabajo actual.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _chdrive(   
   int drive   
);  
```  
  
#### Parámetros  
 `drive`  
 Entero de 1 a 26 que especifica la unidad de trabajo actual \(1\=A, 2\=B, etc.\).  
  
## Valor devuelto  
 Cero \(0\) si la unidad de trabajo actual se ha cambiado correctamente; de lo contrario, \-1.  
  
## Comentarios  
 Si `drive` no está en el intervalo comprendido entre 1 y 26, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función **\_chdrive** devuelve \-1, `errno` se establece en `EACCES` y `_doserrno` se establece en `ERROR_INVALID_DRIVE`.  
  
 La función **\_chdrive** no es segura para subprocesos porque depende de la función **SetCurrentDirectory**, que a su vez no es segura para subprocesos.  Para usar **\_chdrive** de forma segura en una aplicación multiproceso, debe proporcionar su propia sincronización de subprocesos.  Para obtener más información, vaya a [MSDN Library](http://go.microsoft.com/fwlink/?LinkID=150542) y busque **SetCurrentDirectory**.  
  
 La función **\_chdrive** solo cambia la unidad de trabajo actual; **\_chdir** cambia el directorio de trabajo actual.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|**\_chdrive**|\<direct.h\>|  
  
 Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
 Consulte el ejemplo de [\_getdrive](../../c-runtime-library/reference/getdrive.md).  
  
## Equivalente en .NET Framework  
 [System::Environment::CurrentDirectory](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)  
  
## Vea también  
 [Control de directorio](../../c-runtime-library/directory-control.md)   
 [\_chdir, \_wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [\_fullpath, \_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [\_getcwd, \_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [\_getdrive](../../c-runtime-library/reference/getdrive.md)   
 [\_mkdir, \_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [\_rmdir, \_wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)   
 [system, \_wsystem](../../c-runtime-library/reference/system-wsystem.md)