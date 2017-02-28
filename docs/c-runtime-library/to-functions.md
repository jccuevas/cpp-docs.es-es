---
title: to (Funciones) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr120.dll
- msvcr90.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- To
dev_langs:
- C++
helpviewer_keywords:
- to functions
- string conversion, to different characters
- string conversion, case
- lowercase, converting strings
- uppercase, converting strings
- case, converting
- characters, converting
ms.assetid: f636a4c6-8c9f-4be2-baac-064f9dbae300
caps.latest.revision: 13
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
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 0f4efaf826da7a2ff1ef5b9f21bc5e846751211b
ms.lasthandoff: 02/24/2017

---
# <a name="to-functions"></a>to (Funciones)
Cada una de las funciones **to** y su macro asociada, si la hubiera, convierte un carácter individual a otro carácter.  
  
|||  
|-|-|  
|[__toascii](../c-runtime-library/reference/toascii-toascii.md)|[toupper, _toupper, towupper](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|  
|[tolower, _tolower, towlower](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)||  
  
## <a name="remarks"></a>Comentarios  
 Las funciones **to** y las conversiones de macro son las siguientes.  
  
|Rutina|Macro|Descripción|  
|-------------|-----------|-----------------|  
|`__toascii`|`__toascii`|Convierte `c` a caracteres ASCII|  
|`tolower`|`tolower`|Convierte `c` a minúsculas cuando proceda|  
|`_tolower`|`_tolower`|Convierte `c` a minúsculas|  
|`towlower`|Ninguna|Convierte `c` a la correspondiente letra minúscula de caracteres anchos|  
|`toupper`|`toupper`|Convierte `c` a mayúsculas cuando proceda|  
|`_toupper`|`_toupper`|Convierte `c` a mayúsculas|  
|`towupper`|Ninguna|Convierte c a la correspondiente letra mayúscula de caracteres anchos|  
  
 Para usar las versiones de función de las rutinas **to** que también se definen como macros, quite las definiciones de macro con directivas de `#undef` o no incluya CTYPE.H. Si usa la opción del compilador /Za, el compilador usa la versión de función de `toupper` o `tolower`. Las declaraciones de las funciones `toupper` y `tolower` se encuentran en STDLIB.H.  
  
 La rutina `__toascii` establece todos los bits excepto los 7 bits de orden inferior de `c` en 0, por lo que el valor convertido representa un carácter en el juego de caracteres ASCII. Si `c` ya representa un carácter ASCII, `c` no se modifica.  
  
 Las rutinas `tolower` y `toupper`:  
  
-   Dependen de la categoría `LC_CTYPE` de la configuración regional actual (`tolower` llama a `isupper` y `toupper` llama a `islower`).  
  
-   Convierten `c` si `c` representa una letra convertible de las correspondientes mayúsculas y minúsculas en la configuración regional actual y existe el caso contrario para esa configuración regional. De lo contrario, `c` no se modifica.  
  
 Las rutinas `_tolower` y `_toupper`:  
  
-   Son versiones `tolower` y **toupper**, independientes de la configuración regional y mucho más rápidas.  
  
-   Solo se pueden usar cuando **isascii(**`c`**)** y **isupper(**`c`**)** o **islower(**`c`**)**, respectivamente, son distintas de cero.  
  
-   Tienen resultados indefinidos si `c` no es una letra ASCII de las correspondientes mayúsculas y minúsculas para la conversión.  
  
 Las funciones `towlower` y `towupper` devuelven una copia convertida de `c` solo si las dos condiciones siguientes son distintas de cero. De lo contrario, `c` no se modifica.  
  
-   `c` es un carácter ancho de las correspondientes mayúsculas y minúsculas (es decir, para el que `iswupper` o **iswlower**, respectivamente, sean distintas de cero).  
  
-   Hay un carácter ancho correspondiente de las mayúsculas y minúsculas de destino (es decir, para el que `iswlower` o **iswupper**, respectivamente, sean distintas de cero).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_toupper.c  
/* This program uses toupper and tolower to  
 * analyze all characters between 0x0 and 0x7F. It also  
 * applies _toupper and _tolower to any code in this  
 * range for which these functions make sense.  
 */  
  
#include <ctype.h>  
#include <string.h>  
  
char msg[] = "Some of THESE letters are Capitals.";  
char *p;  
  
int main( void )  
{  
   printf( "%s\n", msg );  
  
   /* Reverse case of message. */  
   for( p = msg; p < msg + strlen( msg ); p++ )  
   {  
      if( islower( *p ) )  
         putchar( _toupper( *p ) );  
      else if( isupper( *p ) )  
         putchar( _tolower( *p ) );  
      else  
         putchar( *p );  
   }  
}  
```  
  
```Output  
Some of THESE letters are Capitals.  
sOME OF these LETTERS ARE cAPITALS.  
```  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../c-runtime-library/data-conversion.md)   
 [Configuración regional](../c-runtime-library/locale.md)   
 [is, isw (Rutinas)](../c-runtime-library/is-isw-routines.md)
