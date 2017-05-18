---
title: _getch, _getwch | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _getch
- _getwch
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
- api-ms-win-crt-conio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- getwch
- _getch
- _getwch
dev_langs:
- C++
helpviewer_keywords:
- characters, getting from console
- getch function
- _getwch function
- console, reading from
- _getch function
- getwch function
ms.assetid: cc116be7-cff2-4274-970f-5e7b18ccc05c
caps.latest.revision: 26
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
ms.openlocfilehash: d54444dcd6f0b22527dc2362cfdee5f2b1c33b60
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="getch-getwch"></a>_getch, _getwch
Obtiene un carácter de la consola sin repetición.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _getch( void );  
wint_t _getwch( void );  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el carácter leído. No se devuelve ningún error.  
  
## <a name="remarks"></a>Comentarios  
 El `_getch` y `_getwch` funciones leen un solo carácter de la consola sin repetir el carácter. Ninguna de estas funciones se puede usar para leer CTRL+C. Al leer una tecla de función o de dirección, se debe llamar dos veces a cada función: la primera llamada devuelve 0 o 0xE0, y la segunda devuelve el código de tecla real.  
  
 Estas funciones bloquean el subproceso de llamada y son, por consiguiente, seguras para subprocesos. Para obtener versiones que no sean de bloqueo, consulte [_getch_nolock, _getwch_nolock](../../c-runtime-library/reference/getch-nolock-getwch-nolock.md).  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_gettch`|`_getch`|`_getch`|`_getwch`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_getch`|\<conio.h>|  
|`_getwch`|\<conio.h> o \<wchar.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```C  
// crt_getch.c  
// compile with: /c  
// This program reads characters from  
// the keyboard until it receives a 'Y' or 'y'.  
  
#include <conio.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch;  
  
   _cputs( "Type 'Y' when finished typing keys: " );  
   do  
   {  
      ch = _getch();  
      ch = toupper( ch );  
   } while( ch != 'Y' );  
  
   _putch( ch );  
   _putch( '\r' );    // Carriage return  
   _putch( '\n' );    // Line feed    
}  
```  
  
```Input  
abcdefy
```
  
```Output  
Type 'Y' when finished typing keys: Y  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de consola y de puerto](../../c-runtime-library/console-and-port-i-o.md)   
 [_getche, _getwche](../../c-runtime-library/reference/getche-getwche.md)   
 [_cgets, _cgetws](../../c-runtime-library/cgets-cgetws.md)   
 [getc, getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [_ungetch, _ungetwch, _ungetch_nolock, _ungetwch_nolock](../../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)
