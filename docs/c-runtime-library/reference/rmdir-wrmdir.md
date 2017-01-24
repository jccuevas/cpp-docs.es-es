---
title: "_rmdir, _wrmdir | Microsoft Docs"
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
  - "_wrmdir"
  - "_rmdir"
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
  - "trmdir"
  - "_trmdir"
  - "wrmdir"
  - "_rmdir"
  - "_wrmdir"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_rmdir (función)"
  - "_trmdir (función)"
  - "_wrmdir (función)"
  - "directorios [C++], eliminar"
  - "directorios [C++], quitar"
  - "rmdir (función)"
  - "trmdir (función)"
  - "wrmdir (función)"
ms.assetid: 652c2a5a-b0ac-4493-864e-1edf484333c5
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _rmdir, _wrmdir
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Elimina un directorio.  
  
## Sintaxis  
  
```  
  
      int _rmdir(  
   const char *dirname   
);  
int _wrmdir(  
   const wchar_t *dirname   
);  
```  
  
#### Parámetros  
 `dirname`  
 Ruta de acceso del directorio que se va a quitar.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve 0 si el directorio se elimina correctamente.  Un valor devuelto de – 1 indica que un error y `errno` está establecido en uno de los siguientes valores:  
  
 **ENOTEMPTY**  
 La ruta de acceso especificada no es un directorio, el directorio no está vacío, o el directorio es el directorio de trabajo actual o el directorio raíz.  
  
 `ENOENT`  
 La ruta de acceso no es válida.  
  
 **EACCES**  
 Un programa tiene un identificador abierto al directorio.  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función de `_rmdir` elimina el directorio especificado por `dirname`.  El directorio debe estar vacío, y no debe ser el directorio de trabajo actual o el directorio raíz.  
  
 `_wrmdir` es una versión con caracteres anchos de `_rmdir`; el argumento `dirname` para `_wrmdir` es una cadena de caracteres anchos.  Por lo demás, `_wrmdir` y `_rmdir` se comportan de forma idéntica.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_trmdir`|`_rmdir`|`_rmdir`|`_wrmdir`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_rmdir`|\<direct.h\>|  
|`_wrmdir`|\<direct.h\> o \<wchar.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
 Vea el ejemplo para [\_mkdir](../../c-runtime-library/reference/mkdir-wmkdir.md).  
  
## Equivalente en .NET Framework  
 [System::IO::Directory::Delete](https://msdn.microsoft.com/en-us/library/system.io.directory.delete.aspx)  
  
## Vea también  
 [Control de directorio](../../c-runtime-library/directory-control.md)   
 [\_chdir, \_wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [\_mkdir, \_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)