---
title: "_TRUNCATE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_TRUNCATE"
  - "TRUNCATE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_TRUNCATE (constante)"
  - "TRUNCATE (constante)"
ms.assetid: ad093dbf-1aa5-4bd2-9268-efc68afd8434
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# _TRUNCATE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica el comportamiento del truncamiento de la cadena.  
  
## Sintaxis  
  
```  
#include <stdlib.h>  
```  
  
## Comentarios  
 `_TRUNCATE` habilita el comportamiento de truncamiento cuando se pasa como parámetro de `count` a estas funciones:  
  
 [strncpy\_s, \_strncpy\_s\_l, wcsncpy\_s, \_wcsncpy\_s\_l, \_mbsncpy\_s, \_mbsncpy\_s\_l](../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)  
  
 [strncat\_s, \_strncat\_s\_l, wcsncat\_s, \_wcsncat\_s\_l, \_mbsncat\_s, \_mbsncat\_s\_l](../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)  
  
 [mbstowcs\_s, \_mbstowcs\_s\_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)  
  
 [mbsrtowcs\_s](../c-runtime-library/reference/mbsrtowcs-s.md)  
  
 [wcstombs\_s, \_wcstombs\_s\_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)  
  
 [wcsrtombs\_s](../c-runtime-library/reference/wcsrtombs-s.md)  
  
 [\_snprintf\_s, \_snprintf\_s\_l, \_snwprintf\_s, \_snwprintf\_s\_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)  
  
 [vsnprintf\_s, \_vsnprintf\_s, \_vsnprintf\_s\_l, \_vsnwprintf\_s, \_vsnwprintf\_s\_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)  
  
 Si el búfer de destino es demasiado pequeño para contener la cadena completa, el comportamiento normal de estas funciones es tratarlo como una situación de error \(vea [Validación de parámetros](../c-runtime-library/parameter-validation.md)\).  Sin embargo, si el truncamiento de la cadena se habilita pasando `_TRUNCATE`, estas funciones se copiará solo tanto de la cadena que caben, dejando el búfer de destino terminada en null, y vuelva correctamente.  
  
 El truncamiento de la cadena cambia los valores devueltos de funciones afectadas.  Las siguientes funciones devuelven 0 si ningún truncamiento aparece, o `STRUNCATE` si el truncamiento se produce:  
  
 [strncpy\_s, \_strncpy\_s\_l, wcsncpy\_s, \_wcsncpy\_s\_l, \_mbsncpy\_s, \_mbsncpy\_s\_l](../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)  
  
 [strncat\_s, \_strncat\_s\_l, wcsncat\_s, \_wcsncat\_s\_l, \_mbsncat\_s, \_mbsncat\_s\_l](../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)  
  
 [wcstombs\_s, \_wcstombs\_s\_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)  
  
 [mbstowcs\_s, \_mbstowcs\_s\_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)  
  
 Las siguientes funciones devuelven el número de caracteres copiado si ningún truncamiento aparece, o \-1 si el truncamiento aparece \(haciendo coincidir el comportamiento de las funciones originales de snprintf\):  
  
 [\_snprintf\_s, \_snprintf\_s\_l, \_snwprintf\_s, \_snwprintf\_s\_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)  
  
 [vsnprintf\_s, \_vsnprintf\_s, \_vsnprintf\_s\_l, \_vsnwprintf\_s, \_vsnwprintf\_s\_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)  
  
## Ejemplo  
  
```  
// crt_truncate.c  
#include <stdlib.h>  
#include <errno.h>  
  
int main()  
{  
   char src[] = "1234567890";  
   char dst[5];  
   errno_t err = strncpy_s(dst, _countof(dst), src, _TRUNCATE);  
   if ( err == STRUNCATE )  
      printf( "truncation occurred!\n" );  
   printf( "'%s'\n", dst );  
}  
```  
  
  **el truncamiento se produjo\!**  
**'1234'**   
## Vea también  
 [Constantes globales](../c-runtime-library/global-constants.md)