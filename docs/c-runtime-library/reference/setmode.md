---
title: _setmode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _setmode
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _setmode
dev_langs:
- C++
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: f6d84d5f40b49edaf4e79059a6661a51ca6c209a
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="setmode"></a>_setmode
Establece el modo de traducción del archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _setmode (  
   int fd,  
   int mode   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fd`  
 Descriptor del archivo.  
  
 `mode`  
 Nuevo modo de traducción.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve el modo de traducción anterior.  
  
 Si se pasan parámetros no válidos a esta función, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve -1 y establece `errno` como `EBADF`, lo que indica un descriptor de archivo no válido o `EINVAL`, lo que indica que no es válida `mode` argumento.  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 La función `_setmode` establece en `mode` el modo de traducción del archivo proporcionado por `fd`. Si se pasa `_O_TEXT` como `mode`, se establece el modo de texto (esto es, traducido). Carro retorno-combinaciones de línea (CR-LF) se convierten en una sola línea carácter de salto en la entrada. Los caracteres de salto de línea se traducen a combinaciones CR-LF en la salida. Si se pasa `_O_BINARY`, se establece el modo binario (sin traducir), donde se eliminan las traducciones.  
  
 También puede pasar `_O_U16TEXT`, `_O_U8TEXT`, o `_O_WTEXT` para habilitar el modo Unicode, como se muestra en el segundo ejemplo más adelante en este documento. `_setmode` se suele usar para cambiar el modo de traducción predeterminado de `stdin` y `stdout`, pero se puede usar en cualquier archivo. Si aplica `_setmode` al descriptor de archivo de un flujo, llame a `_setmode` antes de realizar una operación de entrada o de salida en el flujo.  
  
> [!CAUTION]
>  Si escribe datos en un flujo de archivo, vuelque el código explícitamente con [fflush](../../c-runtime-library/reference/fflush.md) antes de usar `_setmode` para cambiar el modo. Si no vuelca el código, podría producirse un comportamiento inesperado. Si no ha escrito datos en el flujo, no será necesario volcarlo.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|Encabezados opcionales|  
|-------------|---------------------|----------------------|  
|`_setmode`|\<io.h>|\<fcntl.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
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
  
```Output  
'stdin' successfully changed to binary mode  
```  
  
## <a name="example"></a>Ejemplo  
  
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
  
## <a name="see-also"></a>Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [_creat, _wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [fopen, _wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_set_fmode](../../c-runtime-library/reference/set-fmode.md)
