---
title: "_set_fmode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_fmode"
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
  - "_set_fmode"
  - "set_fmode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_set_fmode (función)"
  - "traducción de archivos [C++], modo predeterminado"
  - "traducción de archivos [C++], establecer modo"
  - "set_fmode (función)"
ms.assetid: f80eb9c7-733b-4652-a9bc-6b3790a35f12
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _set_fmode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece el archivo predeterminado de modalidad de traducción para operaciones de E\/S de archivos.  
  
## Sintaxis  
  
```  
errno_t _set_fmode(   
   int mode   
);  
```  
  
#### Parámetros  
 \[in\] `mode`  
 El de modalidad de traducción de archivo deseada: `_O_TEXT` o `_O_BINARY`.  
  
## Valor devuelto  
 Devuelve cero si es correcto, un código de error del error.  Si `mode` no es `_O_TEXT` o `_O_BINARY` o `_O_WTEXT`, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función establece `errno` en `EINVAL` y devuelve `EINVAL`.  
  
## Comentarios  
 La función asigna la variable global de [\_fmode](../../c-runtime-library/fmode.md) .  Esta variable especifica el archivo predeterminado de modalidad de traducción para las operaciones de E\/S `_open` y `_pipe`del archivo.  
  
 `_O_TEXT` y `_O_BINARY` se definen en Fcntl.h.  `EINVAL` se define en Errno.h.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_set_fmode`|\<stdlib.h\>|\<fcntl.h, errno.h\>\<\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_set_fmode.c  
#include <stdlib.h>  
#include <stdio.h>  
#include <fcntl.h>     /* for _O_TEXT and _O_BINARY */  
#include <errno.h>     /* for EINVAL */  
#include <sys\stat.h>  /* for _S_IWRITE */  
#include <share.h>     /* for _SH_DENYNO */  
  
int main()  
{  
   int mode, fd, ret;  
   errno_t err;  
   int buf[12] = { 65, 66, 67, 68, 69, 70, 71, 72, 73, 74,  
                   75, 76 };  
   char * filename = "fmode.out";  
  
   err = _get_fmode(&mode);  
   if (err == EINVAL)  
   {  
      printf( "Invalid parameter: mode\n");  
      return 1;  
   }  
   else  
      printf( "Default Mode is %s\n", mode == _O_TEXT ? "text" :  
              "binary");  
  
   err = _set_fmode(_O_BINARY);  
   if (err == EINVAL)  
   {  
      printf( "Invalid mode.\n");  
      return 1;  
   }  
  
   if ( _sopen_s(&fd, filename, _O_RDWR | _O_CREAT, _SH_DENYNO, _S_IWRITE | _S_IREAD) != 0 )  
   {  
      printf( "Error opening the file %s\n", filename);  
      return 1;  
   }  
  
   if (ret = _write(fd, buf, 12*sizeof(int)) < 12*sizeof(int))  
   {  
      printf( "Problem writing to the file %s.\n", filename);  
      printf( "Number of bytes written: %d\n", ret);  
   }  
  
   if (_close(fd) != 0)  
   {  
      printf("Error closing the file %s. Error code %d.\n",  
             filename, errno);  
   }  
  
   system("type fmode.out");  
}  
```  
  
  **El modo predeterminado es binario**  
**UN L OF TABLE K OF TABLE J OF TABLE H I OF TABLE G OF TABLE F OF TABLE D E IZQUIERDA C OF TABLE B**    
## Vea también  
 [\_fmode](../../c-runtime-library/fmode.md)   
 [\_get\_fmode](../../c-runtime-library/reference/get-fmode.md)   
 [\_setmode](../../c-runtime-library/reference/setmode.md)   
 [E\/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md)