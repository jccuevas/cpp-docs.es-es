---
title: "to (Funciones) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
apitype: "DLLExport"
f1_keywords: 
  - "To"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "mayúsculas y minúsculas, convertir"
  - "caracteres, convertir"
  - "minúsculas, convertir cadenas"
  - "conversión de cadenas, mayúsculas y minúsculas"
  - "conversión de cadenas, a distintos caracteres"
  - "a funciones"
  - "mayúsculas, convertir cadenas"
ms.assetid: f636a4c6-8c9f-4be2-baac-064f9dbae300
caps.latest.revision: 13
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# to (Funciones)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cada una de las funciones de **a** y su macro asociada, si existe, convierte un carácter individual a otro carácter.  
  
|||  
|-|-|  
|[\_\_toascii](../c-runtime-library/reference/toascii-toascii.md)|[toupper, \_toupper, towupper](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|  
|[tolower, \_tolower, towlower](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)||  
  
## Comentarios  
 **a** Funciona y las conversiones de macro son los siguientes.  
  
|Rutina|Macro|Descripción|  
|------------|-----------|-----------------|  
|`__toascii`|`__toascii`|Convierte `c` el carácter ASCII|  
|`tolower`|`tolower`|Convierte `c` a minúsculas si es adecuado|  
|`_tolower`|`_tolower`|Convierte `c` en minúsculas|  
|`towlower`|None|Convierte `c` a minúsculas correspondiente de caracteres anchos|  
|`toupper`|`toupper`|Convierte `c` a mayúsculas si es adecuado|  
|`_toupper`|`_toupper`|Convierte `c` a mayúsculas|  
|`towupper`|None|Convierte c a la letra mayúscula de carácter ancho correspondiente|  
  
 Para utilizar las versiones de la función de las rutinas de **a** que también se definen como macros, quite las definiciones de macro con las directivas de `#undef` o no incluya CTYPE.H.  Si utiliza la opción del compilador \/Za, el compilador usa la versión de la función de `toupper` o de `tolower`.  Las declaraciones de las funciones de `toupper` y de `tolower` están en STDLIB.H.  
  
 La rutina de `__toascii` establece todos pero los 7 bits de orden inferior de `c` a 0, de modo que el valor convertido representa un carácter en el juego de caracteres ASCII.  Si `c` representa ya un carácter ASCII, `c` no cambia.  
  
 Las rutinas de `tolower` y de `toupper` :  
  
-   Sea dependiente de la categoría de `LC_CTYPE` de la configuración regional actual \(`tolower` llama `isupper` y `toupper` llama `islower`\).  
  
-   Convierte `c` si `c` representa una letra convertible de casos adecuado en la configuración regional actual y el caso contrario existe para dicha configuración.  Si no, `c` no cambia.  
  
 Las rutinas de `_tolower` y de `_toupper` :  
  
-   Son la configuración regional\-independiente, versiones mucho más rápidas de `tolower` y **toupper.**  
  
-   Solo se puede utilizar cuando **isascii\(**`c`**\)** and either **isupper\(**`c`**\)** or **islower\(**`c`**\)**, respectivamente, es distinto de cero.  
  
-   Tenga resultados no definidos si `c` no es una letra ASCII de casos adecuado para convertir.  
  
 Las funciones de `towlower` y de `towupper` devuelven una copia convierte de `c` si y solo si ambas condiciones siguientes son cero.  Si no, `c` no cambia.  
  
-   `c` es un carácter ancho de casos apropiado \(es decir, para qué `iswupper` o **iswlower,** respectivamente, es distinto de cero\).  
  
-   Hay un carácter ancho correspondiente del caso de destino \(es decir, para qué `iswlower` o **iswupper,** respectivamente, es distinto de cero\).  
  
## Ejemplo  
  
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
  
  **Algunas de letras de THESE son mayúsculas.**  
**algunos de estos mayúsculas de las LETRAS.**   
## Vea también  
 [Conversión de datos](../c-runtime-library/data-conversion.md)   
 [Configuración regional](../c-runtime-library/locale.md)   
 [is, isw \(Rutinas\)](../c-runtime-library/is-isw-routines.md)