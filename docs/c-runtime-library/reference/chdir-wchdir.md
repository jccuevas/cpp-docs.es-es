---
title: "_chdir, _wchdir | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wchdir"
  - "_chdir"
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
  - "tchdir"
  - "_chdir"
  - "_wchdir"
  - "_tchdir"
  - "wchdir"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tchdir (función)"
  - "_chdir (función)"
  - "_wchdir (función)"
  - "tchdir (función)"
  - "wchdir (función)"
  - "chdir (función)"
  - "directorios [C++], cambiar"
ms.assetid: 85e9393b-62ac-45d5-ab2a-fa2217f6152e
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# _chdir, _wchdir
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cambia el directorio de trabajo actual.  
  
## Sintaxis  
  
```  
int _chdir(   
   const char *dirname   
);  
int _wchdir(   
   const wchar_t *dirname   
);  
```  
  
#### Parámetros  
 `dirname`  
 Ruta de acceso del nuevo directorio de trabajo.  
  
## Valor devuelto  
 Estas funciones devuelven un valor de 0 si se ejecutan correctamente. Un valor devuelto de –1 indica error. Si la ruta de acceso especificada no se encuentra, `errno`  se establece en `ENOENT`. Si `dirname` es NULL, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno`  se establece en `EINVAL`  y la función devuelve \-1.  
  
## Comentarios  
 La función `_chdir`  cambia el directorio de trabajo actual por el directorio que se especifica mediante `dirname`. El parámetro `dirname` debe hacer referencia a un directorio existente. Esta función puede cambiar el directorio de trabajo actual de cualquier unidad. Si en `dirname` se especifica otra letra de unidad, la letra de unidad predeterminada también se cambia. Por ejemplo, si A es la letra de unidad predeterminada y \\BIN es el directorio de trabajo actual, la siguiente llamada cambia el directorio de trabajo actual a la unidad C y establece C como nueva unidad predeterminada:  
  
```  
_chdir("c:\\temp");  
```  
  
 Si se usa el carácter de barra diagonal inversa opcional \(`\`\) en rutas de acceso, es necesario poner dos barras diagonales inversas \(`\\`\) en un literal de cadena de C para representar una única barra diagonal inversa \(`\`\).  
  
 `_wchdir` es una versión con caracteres anchos de `_chdir`; el argumento de `dirname` para `_wchdir` es una cadena de caracteres anchos`. _wchdir` y `_chdir` se comportan de forma idéntica en todo lo demás.  
  
### Asignación de rutina de texto genérico:  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tchdir`|`_chdir`|`_chdir`|`_wchdir`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_chdir`|\<direct.h\>|\<errno.h\>|  
|`_wchdir`|\<direct.h\> o \<wchar.h\>|\<errno.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_chdir.c  
// arguments: C:\WINDOWS  
  
/* This program uses the _chdir function to verify  
   that a given directory exists. */  
  
#include <direct.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main( int argc, char *argv[] )  
{  
  
   if(_chdir( argv[1] ) )  
   {  
      switch (errno)  
      {  
      case ENOENT:  
         printf( "Unable to locate the directory: %s\n", argv[1] );  
         break;  
      case EINVAL:  
         printf( "Invalid buffer.\n");  
         break;  
      default:  
         printf( "Unknown error.\n");  
      }  
   }  
   else  
      system( "dir *.exe");  
}  
```  
  
```Output  
El volumen de la unidad C no tiene etiqueta. Número de serie del volumen es 2018-08A1 Directorio de c:\windows 08/29/2002  04:00 AM         1,004,032 explorer.exe 12/17/2002  04:43 PM            10,752 hh.exe 03/03/2003  09:24 AM            33,792 ieuninst.exe 10/29/1998  04:45 PM           306,688 IsUninst.exe 08/29/2002  04:00 AM            66,048 NOTEPAD.EXE 03/03/2003  09:24 AM            33,792 Q330994.exe 08/29/2002  04:00 AM           134,144 regedit.exe 02/28/2003  06:26 PM            46,352 setdebug.exe 08/29/2002  04:00 AM            15,360 TASKMAN.EXE 08/29/2002  04:00 AM            49,680 twunk_16.exe 08/29/2002  04:00 AM            25,600 twunk_32.exe 08/29/2002  04:00 AM           256,192 winhelp.exe 08/29/2002  04:00 AM           266,752 winhlp32.exe 13 archivo(s)      2,249,184 bytes 0 drectorio(s)  67,326,029,824 bytes libres  
```  
  
## Equivalente en .NET Framework  
 [System::Environment::CurrentDirectory](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)  
  
## Vea también  
 [Control de directorio](../../c-runtime-library/directory-control.md)   
 [\_mkdir, \_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [\_rmdir, \_wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)   
 [system, \_wsystem](../../c-runtime-library/reference/system-wsystem.md)