---
title: "_splitpath_s, _wsplitpath_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wsplitpath_s"
  - "_splitpath_s"
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
  - "_wsplitpath_s"
  - "splitpath_s"
  - "_splitpath_s"
  - "wsplitpath_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_splitpath_s (función)"
  - "_wsplitpath_s (función)"
  - "nombres de ruta de acceso"
  - "nombres de rutas de acceso"
  - "splitpath_s (función)"
  - "wsplitpath_s (función)"
ms.assetid: 30fff3e2-cd00-4eb6-b5a2-65db79cb688b
caps.latest.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 29
---
# _splitpath_s, _wsplitpath_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Interrumpe un nombre de ruta en componentes.  Éstas son versiones de [\_splitpath, \_wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t _splitpath_s(  
   const char * path,  
   char * drive,  
   size_t driveNumberOfElements,  
   char * dir,  
   size_t dirNumberOfElements,  
   char * fname,  
   size_t nameNumberOfElements,  
   char * ext,   
   size_t extNumberOfElements  
);  
errno_t _wsplitpath_s(  
   const wchar_t * path,  
   wchar_t * drive,  
   size_t driveNumberOfElements,  
   wchar_t *dir,  
   size_t dirNumberOfElements,  
   wchar_t * fname,  
   size_t nameNumberOfElements,  
   wchar_t * ext,  
   size_t extNumberOfElements  
);  
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>  
errno_t _splitpath_s(  
   const char *path,  
   char (&drive)[drivesize],  
   char (&dir)[dirsize],  
   char (&fname)[fnamesize],  
   char (&ext)[extsize]  
); // C++ only  
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>  
errno_t _wsplitpath_s(  
   const wchar_t *path,  
   wchar_t (&drive)[drivesize],  
   wchar_t (&dir)[dirsize],  
   wchar_t (&fname)[fnamesize],  
   wchar_t (&ext)[extsize]  
); // C++ only  
```  
  
#### Parámetros  
 \[in\] `path`  
 Ruta de acceso completa.  
  
 \[out\] `drive`  
 Letra de unidad, seguida de dos puntos \(`:`\).  Puede pasar `NULL` para este parámetro si no necesita la letra de unidad.  
  
 \[in\] `driveNumberOfElements`  
 El tamaño del búfer de `drive` en solo\- bytes o caracteres anchos.  Si `drive` es `NULL`, este valor debe ser 0.  
  
 \[out\] `dir`  
 Ruta de acceso del directorio, incluida la barra diagonal final.  Las barras diagonales \( `/` \), las barras diagonales inversas \( `\` \), o ambas pueden utilizar.  Puede pasar `NULL` para este parámetro si no necesita la ruta del directorio.  
  
 \[in\] `dirNumberOfElements`  
 El tamaño del búfer de `dir` en solo\- bytes o caracteres anchos.  Si `dir` es `NULL`, este valor debe ser 0.  
  
 \[out\] `fname`  
 Nombre de archivo base \(sin extensión\).  Puede pasar `NULL` para este parámetro si no necesita el nombre de archivo.  
  
 \[in\] `nameNumberOfElements`  
 El tamaño del búfer de `fname` en solo\- bytes o caracteres anchos.  Si `fname` es `NULL`, este valor debe ser 0.  
  
 \[out\] `ext`  
 Extensión de nombre de archivo, incluido el punto principal \(**.**\). Puede pasar `NULL` para este parámetro si no necesita la extensión de nombre de archivo.  
  
 \[in\] `extNumberOfElements`  
 El tamaño del búfer de `ext` en solo\- bytes o caracteres anchos.  Si `ext` es `NULL`, este valor debe ser 0.  
  
## Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.  
  
### Condiciones de error  
  
|Condition|Valor devuelto|  
|---------------|--------------------|  
|`path` es `NULL`.|`EINVAL`|  
|`drive` es `NULL`, `driveNumberOfElements` es distinto de cero|`EINVAL`|  
|`drive` es`NULL`no\-, `driveNumberOfElements` es cero|`EINVAL`|  
|`dir` es `NULL`, `dirNumberOfElements` es distinto de cero|`EINVAL`|  
|`dir` es`NULL`no\-, `dirNumberOfElements` es cero|`EINVAL`|  
|`fname` es `NULL`, `nameNumberOfElements` es distinto de cero|`EINVAL`|  
|`fname` es`NULL`no\-, `nameNumberOfElements` es cero|`EINVAL`|  
|`ext` es `NULL`, `extNumberOfElements` es distinto de cero|`EINVAL`|  
|`ext` es`NULL`no\-, `extNumberOfElements` es cero|`EINVAL`|  
  
 Si es un de los sobre condiciones aparece, el controlador no válido de parámetro se invoca, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md) .  Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven `EINVAL`.  
  
 Si los búferes cualquiera de los son demasiado cortos contener el resultado, estas funciones desactive todos los búferes a cadenas vacías, establecen `errno` a `ERANGE`, y devuelven `ERANGE`.  
  
## Comentarios  
 La función de `_splitpath_s` interrumpe una ruta en los cuatro componentes.  `_splitpath_s` controla automáticamente argumentos de cadena de multibyte\- carácter según corresponda, reconociendo secuencias de multibyte\- carácter según la página de códigos multibyte actualmente en uso.  `_wsplitpath_s` es una versión con caracteres anchos de `_splitpath_s`; los argumentos de `_``wsplitpath_s`son cadenas de caracteres.  Estas funciones se comportan exactamente igual de otra forma  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tsplitpath_s`|`_splitpath_s`|`_splitpath_s`|`_wsplitpath_s`|  
  
 Almacena en cada componente de la ruta de acceso completa en un búfer independiente; las constantes del manifiesto `_MAX_DRIVE`, `_MAX_DIR`, `_MAX_FNAME`, y `_MAX_EXT` \(definido en STDLIB.H\) especifique el tamaño máximo permitido para cada componente del archivo.  Los componentes de archivo mayores que las constantes de manifiesto correspondientes producen daños en la pila.  
  
 La tabla siguiente se enumeran los valores de las constantes del manifiesto.  
  
|Name|Valor|  
|----------|-----------|  
|\_MAX\_DRIVE|3|  
|\_MAX\_DIR|256|  
|\_MAX\_FNAME|256|  
|\_MAX\_EXT|256|  
  
 Si la ruta de acceso completa no contiene un componente \(por ejemplo, un nombre de archivo\), `_splitpath_s` asigna una cadena vacía al búfer correspondiente.  
  
 En C\+\+, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
 Las versiones de depuración de estas funciones rellenan primero el búfer con 0xFD.  Para deshabilitar este comportamiento, use [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_splitpath_s`|\<stdlib.h\>|  
|`_wsplitpath_s`|\<stdlib.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Consulte el ejemplo de [\_makepath\_s, \_wmakepath\_s](../../c-runtime-library/reference/makepath-s-wmakepath-s.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [\_splitpath, \_wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)   
 [\_fullpath, \_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [\_makepath, \_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)