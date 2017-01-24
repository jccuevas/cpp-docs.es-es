---
title: "_getdcwd, _wgetdcwd | Microsoft Docs"
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
  - "_getdcwd"
  - "_wgetdcwd"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wgetdcwd"
  - "getdcwd"
  - "_getdcwd"
  - "tgetdcwd"
  - "_wgetdcwd"
  - "_tgetdcwd"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "wgetdcwd (función)"
  - "directorio de trabajo"
  - "getdcwd (función)"
  - "_getdcwd (función)"
  - "_wgetdcwd (función)"
  - "directorio de trabajo actual"
  - "trabajo actuales directorios [C++]"
ms.assetid: 184152f5-c7b0-495b-918d-f9a6adc178bd
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _getdcwd, _wgetdcwd
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene la ruta de acceso completa del directorio de trabajo actual en la unidad especificada.  
  
## Sintaxis  
  
```  
char *_getdcwd(   
   int drive,  
   char *buffer,  
   int maxlen   
);  
wchar_t *_wgetdcwd(   
   int drive,  
   wchar_t *buffer,  
   int maxlen   
);  
```  
  
#### Parámetros  
 `drive`  
 Entero no negativo que especifica la unidad \(0 \= unidad predeterminada, 1 \= A, 2 \= B, etc.\).  
  
 Si la unidad especificada no está disponible, o no se puede determinar la clase de unidad \(por ejemplo, extraíble, fija, CD\-ROM, disco RAM o unidad de red\), se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
 `buffer`  
 Ubicación de almacenamiento para la ruta de acceso o **NULL**.  
  
 Si **NULL** se especifica, esta función asigna un búfer de al menos `maxlen` tamaño utilizando **malloc**, y el valor devuelto de `_getdcwd` es un puntero al búfer asignado. El búfer se puede liberar llamando a `free` y pasándole el puntero.  
  
 `maxlen`  
 Entero positivo distinto de cero que especifica la longitud máxima de la ruta de acceso en caracteres: `char` para `_getdcwd` y `wchar_t` para `_wgetdcwd`.  
  
 Si `maxlen` no es mayor que cero, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
## Valor devuelto  
 Puntero a una cadena que representa la ruta de acceso completa del directorio de trabajo actual en la unidad especificada, o `NULL`, que indica un error.  
  
 Si se especifica `buffer` como `NULL` y no hay memoria suficiente para asignar el número de caracteres de `maxlen`, se produce un error y `errno` se establece en `ENOMEM`. Si la longitud de la ruta de acceso, incluido el carácter nulo de terminación, es mayor que el valor de `maxlen`, se produce un error y `errno` se establece en `ERANGE`. Para obtener más información sobre estos códigos de error, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función `_getdcwd` obtiene la ruta de acceso completa del directorio de trabajo actual en la unidad especificada y la almacena en `buffer`. Si el directorio de trabajo actual es la raíz, la cadena finaliza con una barra diagonal inversa \(\\\). Si el directorio de trabajo actual es un directorio distinto de la raíz, la cadena finaliza con el nombre de directorio y no con una barra diagonal inversa.  
  
 `_wgetdcwd` es una versión con caracteres anchos de `_getdcwd`, y su parámetro `buffer` y su valor devuelto son cadenas de caracteres anchos. De lo contrario, los objetos `_wgetdcwd` y `_getdcwd` se comportan de forma idéntica.  
  
 Esta función es segura para subprocesos, aunque depende de **GetFullPathName**, que es en sí mismo no segura para subprocesos. Sin embargo, puede violar la seguridad de subprocesos si la aplicación multiproceso llama a esta función y **GetFullPathName**. Para obtener más información, vaya a [MSDN Library](http://go.microsoft.com/fwlink/?LinkID=150542) y, a continuación, busque **GetFullPathName**.  
  
 La versión de esta función con el sufijo `_nolock` tiene un comportamiento idéntico al de esta función, salvo que no es segura para subprocesos y no está protegida contra interferencias de otros subprocesos. Para obtener más información, vea [\_getdcwd\_nolock, \_wgetdcwd\_nolock](../../c-runtime-library/reference/getdcwd-nolock-wgetdcwd-nolock.md).  
  
 Cuando se definen `_DEBUG` y `_CRTDBG_MAP_ALLOC`, las llamadas a `_getdcwd` y `_wgetdcwd` se reemplazan por llamadas a `_getdcwd_dbg` y `_wgetdcwd_dbg` para que se puedan depurar las asignaciones de memoria. Para obtener más información, consulte [\_getdcwd\_dbg, \_wgetdcwd\_dbg](../../c-runtime-library/reference/getdcwd-dbg-wgetdcwd-dbg.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tgetdcwd`|`_getdcwd`|`_getdcwd`|`_wgetdcwd`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_getdcwd`|\<direct.h\>|  
|`_wgetdcwd`|\<direct.h\> o \<wchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
 Consulte el ejemplo de [\_getdrive](../../c-runtime-library/reference/getdrive.md).  
  
## Equivalente en .NET Framework  
 [System::Environment::CurrentDirectory](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)  
  
## Vea también  
 [Control de directorio](../../c-runtime-library/directory-control.md)   
 [\_chdir, \_wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [\_getcwd, \_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [\_getdrive](../../c-runtime-library/reference/getdrive.md)   
 [\_mkdir, \_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [\_rmdir, \_wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)