---
title: "_splitpath, _wsplitpath | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wsplitpath"
  - "_splitpath"
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
  - "wsplitpath"
  - "_splitpath"
  - "splitpath"
  - "_wsplitpath"
  - "_tsplitpath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_splitpath (función)"
  - "_tsplitpath (función)"
  - "_wsplitpath (función)"
  - "nombres de ruta de acceso"
  - "nombres de rutas de acceso"
  - "splitpath (función)"
  - "tsplitpath (función)"
  - "wsplitpath (función)"
ms.assetid: 32bd76b5-1385-4ee8-a64c-abcb541cd2e4
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _splitpath, _wsplitpath
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Divida un nombre de ruta en componentes.  Hay disponibles versiones más seguras de estas funciones; vea [\_splitpath\_s, \_wsplitpath\_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md).  
  
## Sintaxis  
  
```  
void _splitpath(  
   const char *path,  
   char *drive,  
   char *dir,  
   char *fname,  
   char *ext   
);  
void _wsplitpath(  
   const wchar_t *path,  
   wchar_t *drive,  
   wchar_t *dir,  
   wchar_t *fname,  
   wchar_t *ext   
);  
```  
  
#### Parámetros  
 `path`  
 Ruta de acceso completa.  
  
 `drive`  
 Letra de unidad, seguida de dos puntos \(`:`\).  Puede pasar `NULL` para este parámetro si no necesita la letra de unidad.  
  
 `dir`  
 Ruta de acceso del directorio, incluida la barra diagonal final.  Las barras diagonales \( `/` \), las barras diagonales inversas \( `\` \), o ambas pueden utilizar.  Puede pasar `NULL` para este parámetro si no necesita la ruta del directorio.  
  
 `fname`  
 Nombre de archivo base \(ninguna extensión\).  Puede pasar `NULL` para este parámetro si no necesita el nombre de archivo.  
  
 `ext`  
 Extensión de nombre de archivo, incluido el punto principal \(`.`\).  Puede pasar `NULL` para este parámetro si no necesita la extensión de nombre de archivo.  
  
## Comentarios  
 La función de `_splitpath` interrumpe una ruta en los cuatro componentes.  `_splitpath` controla automáticamente argumentos de cadena de multibyte\- carácter según corresponda, reconociendo secuencias de multibyte\- carácter según la página de códigos multibyte actualmente en uso.  `_wsplitpath` es una versión con caracteres anchos de `_splitpath`; los argumentos a `_wsplitpath` son cadenas de caracteres anchos.  Por lo demás, estas funciones se comportan exactamente igual.  
  
 **Nota de seguridad** Estas funciones representan una posible amenaza por un problema de saturación del búfer.  Los problemas de saturación del búfer son un método frecuente de ataque del sistema, que produce una elevación de privilegios no justificada.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  Versiones más seguras de estas funciones están disponibles; vea [\_splitpath\_s, \_wsplitpath\_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tsplitpath`|`_splitpath`|`_splitpath`|`_wsplitpath`|  
  
 Almacena en cada componente de la ruta de acceso completa en un búfer independiente; las constantes del manifiesto `_MAX_DRIVE`, `_MAX_DIR`, `_MAX_FNAME`, y `_MAX_EXT` \(definido en STDLIB.H\) especifica el tamaño máximo para cada componente del archivo.  Los componentes de los archivos que son mayores que las constantes de manifiesto correspondientes producen daños en la pila.  
  
 Cada búfer debe ser tan grande como la constante de manifiesto correspondiente evitar la saturación del búfer potencial.  
  
 La tabla siguiente se enumeran los valores de las constantes del manifiesto.  
  
|Name|Valor|  
|----------|-----------|  
|\_MAX\_DRIVE|3|  
|\_MAX\_DIR|256|  
|\_MAX\_FNAME|256|  
|\_MAX\_EXT|256|  
  
 Si la ruta de acceso completa no contiene un componente \(por ejemplo, un nombre de archivo\), `_splitpath` asigna cadenas vacías a los búferes correspondientes.  
  
 Puede pasar `NULL` a `_splitpath` para cualquier parámetro distinto de `path` que no necesite.  
  
 Si `path` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `EINVAL`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_splitpath`|\<stdlib.h\>|  
|`_wsplitpath`|\<stdlib.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea el ejemplo para [\_makepath](../../c-runtime-library/reference/makepath-wmakepath.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [\_fullpath, \_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [\_makepath, \_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [\_splitpath\_s, \_wsplitpath\_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)