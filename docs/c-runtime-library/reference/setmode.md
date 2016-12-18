---
title: "_setmode | Microsoft Docs"
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
  - "_setmode"
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
  - "_setmode"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_setmode (función)"
  - "traducción de archivos [C++], establecer modo"
  - "archivos [C++], modos"
  - "archivos [C++], traslación"
  - "setmode (función)"
  - "Unicode [C++], salida de consola"
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
caps.latest.revision: 23
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _setmode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece el modo de traducción del archivo.  
  
## Sintaxis  
  
```  
int _setmode (    int fd,    int mode  );  
```  
  
#### Parámetros  
 `fd`  
 Descriptor del archivo.  
  
 `mode`  
 Nuevo modo de traducción.  
  
## Valor devuelto  
 Si es correcto, devuelve el modo de traducción anterior.  
  
 Si se pasan parámetros no válidos a esta función, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, esta función devuelve –1 y establece `errno` en `EBADF` \(que indica un descriptor de archivo no válido\) o en `EINVAL` \(que indica un argumento `mode` no válido\).  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función `_setmode` establece en `mode` el modo de traducción del archivo proporcionado por `fd`.  Si se pasa `_O_TEXT` como `mode`, se establece el modo de texto \(esto es, traducido\).  Las combinaciones retorno de carro\-salto de línea \(CR\-LF\) se traducen en un carácter de salto de línea único en la entrada.  Los caracteres de salto de línea se traducen a combinaciones CR\-LF en la salida.  Si se pasa `_O_BINARY`, se establece el modo binario \(sin traducir\), donde se eliminan las traducciones.  
  
 También se puede pasar `_O_U16TEXT`, `_O_U8TEXT` o \_`O_WTEXT` para habilitar el modo Unicode, tal y como se refleja en el segundo ejemplo recogido más adelante en este documento.  `_setmode` se suele usar para cambiar el modo de traducción predeterminado de `stdin` y `stdout`, pero se puede usar en cualquier archivo.  Si aplica `_setmode` al descriptor de archivo de un flujo, llame a `_setmode` antes de realizar una operación de entrada o de salida en el flujo.  
  
> [!CAUTION]
>  Si escribe datos en un flujo de archivo, vuelque el código expresamente mediante [fflush](../../c-runtime-library/reference/fflush.md) antes de usar `_setmode` para cambiar el modo.  Si no vuelca el código, podría producirse un comportamiento inesperado.  Si no ha escrito datos en el flujo, no será necesario volcarlo.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezados opcionales|  
|------------|--------------------------|----------------------------|  
|`_setmode`|\<io.h\>|\<fcntl.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_setmode.c  
// This program uses _setmode to change  
// stdin from text mode to binary mode.  
  
#include <stdio.h>  
#include <fcntl.h>  
#include <io.h>  
  
int main( void )  
{  
   int result;  
  
   // Set "stdin" to have binary mode:  
   result = _setmode( _fileno( stdin ), _O_BINARY );  
   if( result == -1 )  
      perror( "Cannot set mode" );  
   else  
      printf( "'stdin' successfully changed to binary mode\n" );  
}  
```  
  
  **'stdin' successfully changed to binary mode**   
## Ejemplo  
  
```  
// crt_setmodeunicode.c  
// This program uses _setmode to change  
// stdout to Unicode. Cyrillic and Ideographic  
// characters will appear on the console (if  
// your console font supports those character sets).  
  
#include <fcntl.h>  
#include <io.h>  
#include <stdio.h>  
  
int main(void) {  
    _setmode(_fileno(stdout), _O_U16TEXT);  
    wprintf(L"\x043a\x043e\x0448\x043a\x0430 \x65e5\x672c\x56fd\n");  
    return 0;  
}  
  
```  
  
## Equivalente de .NET Framework  
  
-   [\<caps:sentence id\="tgt28" sentenceid\="fe03c471a7a38d5378cea62467482dae" class\="tgtSentence"\>System::IO::BinaryReader Class\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.io.binaryreader.aspx)  
  
-   [\<caps:sentence id\="tgt29" sentenceid\="105e62b7505c25e3e182779c87f145eb" class\="tgtSentence"\>System::IO::TextReader Class\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.io.textreader.aspx)  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [\_creat, \_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [fopen, \_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [\_open, \_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_set\_fmode](../../c-runtime-library/reference/set-fmode.md)