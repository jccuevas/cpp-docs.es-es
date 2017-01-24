---
title: "_strdec, _wcsdec, _mbsdec, _mbsdec_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wcsdec"
  - "_strdec"
  - "_mbsdec"
  - "_mbsdec_l"
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
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_strdec"
  - "mbsdec_l"
  - "strdec"
  - "_mbsdec"
  - "_mbsdec_l"
  - "mbsdec"
  - "wcsdec"
  - "_wcsdec"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsdec (función)"
  - "_mbsdec_l (función)"
  - "_strdec (función)"
  - "_tcsdec (función)"
  - "_wcsdec (función)"
  - "mbsdec (función)"
  - "mbsdec_l (función)"
  - "strdec (función)"
  - "tcsdec (función)"
  - "wcsdec (función)"
ms.assetid: ae37c223-800f-48a9-ae8e-38c8d20af2dd
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strdec, _wcsdec, _mbsdec, _mbsdec_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Hace retroceder el puntero de cadena un carácter.  
  
> [!IMPORTANT]
>  `mbsdec` y `mbsdec_l` no se pueden usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
unsigned char *_strdec(  
   const unsigned char *start,  
   const unsigned char *current   
);  
unsigned wchar_t *_wcsdec(  
   const unsigned wchar_t *start,  
   const unsigned wchar_t *current   
);  
unsigned char *_mbsdec(  
   const unsigned char *start,  
   const unsigned char *current   
);  
unsigned char *_mbsdec_l(  
   const unsigned char *start,  
   const unsigned char *current,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `start`  
 Puntero a cualquier carácter \(en el caso de `_mbsdec` y \_`mbsdec_l`, al primer byte de cualquier carácter multibyte\) de la cadena de origen; `start` debe preceder a `current` en la cadena de origen.  
  
 `current`  
 Puntero a cualquier carácter \(en el caso de `_mbsdec` y \_`mbsdec_l`, al primer byte de cualquier carácter multibyte\) de la cadena de origen; `current` debe seguir a `start` en la cadena de origen.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 `_mbsdec`, \_`mbsdec_l`, `_strdec` y `_wcsdec` devuelven un puntero al carácter que precede inmediatamente a `current`; `_mbsdec` devuelve `NULL` si el valor de `start` es mayor o igual que el de `current`.  los mapas de`_tcsdec` se asigna a una de estas funciones y el valor que devuelve depende de la asignación.  
  
## Comentarios  
 Las funciones `_mbsdec` y `_mbsdec_l` devuelven un puntero al primer byte del carácter multibyte que precede inmediatamente a `current` en la cadena que contiene `start`.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional. Vea [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información. `_mbsdec` reconoce secuencias de caracteres multibyte en función de la configuración regional actualmente en uso, y `_mbsdec_l` es idéntica, salvo que usa el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 Si `start` o `current` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve `EINVAL` y establece `errno` en `EINVAL`.  
  
> [!IMPORTANT]
>  Estas funciones pueden ser vulnerables a amenazas de saturación del búfer.  Las saturaciones del búfer se pueden usar para ataques del sistema, ya que pueden producir una elevación de privilegios no justificada.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsdec`|`_strdec`|`_mbsdec`|`_wcsdec`|  
  
 `_strdec` y `_wcsdec` son versiones de caracteres de un solo byte y caracteres anchos de `_mbsdec` y `_mbsdec_l`.  `_strdec` y `_wcsdec` se proporcionan solo para esta asignación y no deben usarse de otra manera.  
  
 Para obtener más información, vea [Usar asignaciones de texto genérico](../../c-runtime-library/using-generic-text-mappings.md) y [Asignaciones de texto genérico](../../c-runtime-library/generic-text-mappings.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_mbsdec`|\<mbstring.h\>|\<mbctype.h\>|  
|`_mbsdec_l`|\<mbstring.h\>|\<mbctype.h\>|  
|`_strdec`|\<tchar.h\>||  
|`_wcsdec`|\<tchar.h\>||  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
 En el siguiente ejemplo, se muestra el uso de `_tcsdec`.  
  
```  
#include <iostream>  
#include <tchar.h>  
using namespace std;  
  
int main()  
{  
   const TCHAR *str = _T("12345");  
   cout << "str: " << str << endl;  
  
   const TCHAR *str2;  
   str2 = str + 2;  
   cout << "str2: " << str2 << endl;  
  
   TCHAR *answer;  
   answer = _tcsdec( str, str2 );  
   cout << "answer: " << answer << endl;  
  
   return (0);   
}  
  
```  
  
 En el siguiente ejemplo, se muestra el uso de `_mbsdec`.  
  
```  
#include <iostream>  
#include <mbstring.h>  
using namespace std;  
  
int main()   
{   
   char *str = "12345";  
   cout << "str: " << str << endl;  
  
   char *str2;  
   str2 = str + 2;   
   cout << "str2: " << str2 << endl;  
  
   unsigned char *answer;  
   answer = _mbsdec( reinterpret_cast<unsigned char *>( str ), reinterpret_cast<unsigned char *>( str2 ));  
  
   cout << "answer: " << answer << endl;  
  
   return (0);   
}  
  
```  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [\_strinc, \_wcsinc, \_mbsinc, \_mbsinc\_l](../../c-runtime-library/reference/strinc-wcsinc-mbsinc-mbsinc-l.md)   
 [\_strnextc, \_wcsnextc, \_mbsnextc, \_mbsnextc\_l](../../c-runtime-library/reference/strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)   
 [\_strninc, \_wcsninc, \_mbsninc, \_mbsninc\_l](../../c-runtime-library/reference/strninc-wcsninc-mbsninc-mbsninc-l.md)