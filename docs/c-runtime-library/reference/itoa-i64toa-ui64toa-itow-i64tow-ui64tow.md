---
title: "_itoa, _i64toa, _ui64toa, _itow, _i64tow, _ui64tow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_itow"
  - "_i64tow"
  - "_itoa"
  - "_i64toa"
  - "_ui64toa"
  - "_ui64tow"
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
  - "api-ms-win-crt-convert-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_i64tow"
  - "ui64toa"
  - "ui64tow"
  - "itot"
  - "_itot"
  - "_i64toa"
  - "_itoa"
  - "_itow"
  - "_ui64tow"
  - "i64toa"
  - "i64tow"
  - "itow"
  - "_ui64toa"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_i64toa (función)"
  - "_i64tow (función)"
  - "_itoa (función)"
  - "_itot (función)"
  - "_itow (función)"
  - "_ui64toa (función)"
  - "_ui64tow (función)"
  - "convertir enteros"
  - "convertir números, a cadenas"
  - "i64toa (función)"
  - "i64tow (función)"
  - "enteros, convertir"
  - "itoa (función)"
  - "itot (función)"
  - "itow (función)"
  - "ui64toa (función)"
  - "ui64tow (función)"
ms.assetid: 46592a00-77bb-4e73-98c0-bf629d96cea6
caps.latest.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 25
---
# _itoa, _i64toa, _ui64toa, _itow, _i64tow, _ui64tow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte un entero en cadena.  Hay disponibles versiones más seguras de estas funciones; vea [\_itoa\_s, \_i64toa\_s, \_ui64toa\_s, \_itow\_s, \_i64tow\_s, \_ui64tow\_s](../../c-runtime-library/reference/itoa-s-i64toa-s-ui64toa-s-itow-s-i64tow-s-ui64tow-s.md).  
  
## Sintaxis  
  
```  
char *_itoa(  
   int value,  
   char *str,  
   int radix   
);  
char *_i64toa(  
   __int64 value,  
   char *str,  
   int radix   
);  
char * _ui64toa(  
   unsigned _int64 value,  
   char *str,  
   int radix   
);  
wchar_t * _itow(  
   int value,  
   wchar_t *str,  
   int radix   
);  
wchar_t * _i64tow(  
   __int64 value,  
   wchar_t *str,  
   int radix   
);  
wchar_t * _ui64tow(  
   unsigned __int64 value,  
   wchar_t *str,  
   int radix   
);  
template <size_t size>  
char *_itoa(  
   int value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
char *_i64toa(  
   __int64 value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
char * _ui64toa(  
   unsigned _int64 value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t * _itow(  
   int value,  
   wchar_t (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t * _i64tow(  
   __int64 value,  
   wchar_t (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t * _ui64tow(  
   unsigned __int64 value,  
   wchar_t (&str)[size],  
   int radix   
); // C++ only  
```  
  
#### Parámetros  
 `value`  
 Número que se va a convertir.  
  
 `str`  
 Cadena de resultado.  
  
 `radix`  
 Base de `value`; debe estar comprendido entre 2 y 36.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve un puntero a `str`.  No se devuelve ningún error.  
  
## Comentarios  
 Las funciones `_itoa`, `_i64toa` y `_ui64toa` convierten los dígitos de argumento de `value` dado en una cadena de caracteres terminada en un carácter nulo y almacenan el resultado \(hasta 33 caracteres en el caso de `_itoa` y 65 en el de `_i64toa` y `_ui64toa`\) en `str`.  Si `radix` es igual a 10 y `value` es negativo, el primer carácter de la cadena almacenada es el signo menos \( `–`\).  `_itow`, `_i64tow` y `_ui64tow` son versiones con caracteres anchos de `_itoa`, `_i64toa` y `_ui64toa`, respectivamente.  
  
> [!IMPORTANT]
>  Para evitar las saturaciones del búfer, asegúrese de que el búfer de `str` tiene el tamaño suficiente para contener los dígitos convertidos más el carácter nulo final y un carácter de signo.  
  
 En C\+\+, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_itot`|`_itoa`|`_itoa`|`_itow`|  
|`_i64tot`|`_i64toa`|`_i64toa`|`_i64tow`|  
|`_ui64tot`|`_ui64toa`|`_ui64toa`|`_ui64tow`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_itoa`|\<stdlib.h\>|  
|`_i64toa`|\<stdlib.h\>|  
|`_ui64toa`|\<stdlib.h\>|  
|`_itow`|\<stdlib.h\>|  
|`_i64tow`|\<stdlib.h\>|  
|`_ui64tow`|\<stdlib.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_itoa.c  
// compile with: /W3  
// This program makes use of the _itoa functions  
// in various examples.  
  
#include <string.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char buffer[65];  
   int r;  
   for( r=10; r>=2; --r )  
   {  
     _itoa( -1, buffer, r ); // C4996  
     // Note: _itoa is deprecated; consider using _itoa_s instead  
     printf( "base %d: %s (%d chars)\n", r, buffer, strnlen(buffer, _countof(buffer)) );  
   }  
   printf( "\n" );  
   for( r=10; r>=2; --r )  
   {  
     _i64toa( -1L, buffer, r ); // C4996  
     // Note: _i64toa is deprecated; consider using _i64toa_s  
     printf( "base %d: %s (%d chars)\n", r, buffer, strnlen(buffer, _countof(buffer)) );  
   }  
   printf( "\n" );  
   for( r=10; r>=2; --r )  
   {  
     _ui64toa( 0xffffffffffffffffL, buffer, r ); // C4996  
     // Note: _ui64toa is deprecated; consider using _ui64toa_s  
     printf( "base %d: %s (%d chars)\n", r, buffer, strnlen(buffer, _countof(buffer)) );  
   }  
}  
```  
  
  **base 10: \-1 \(2 caracteres\)**  
**base 9: 12068657453 \(11 caracteres\)**  
**base 8: 37777777777 \(11 caracteres\)**  
**base 7: 211301422353 \(12 caracteres\)**  
**base 6: 1550104015503 \(13 caracteres\)**  
**base 5: 32244002423140 \(14 caracteres\)**  
**base 4: 3333333333333333 \(16 caracteres\)**  
**base 3: 102002022201221111210 \(21 caracteres\)**  
**base 2: 11111111111111111111111111111111 \(32 caracteres\)**  
**base 10: \-1 \(2 caracteres\)**  
**base 9: 145808576354216723756 \(21 caracteres\)**  
**base 8: 1777777777777777777777 \(22 caracteres\)**  
**base 7: 45012021522523134134601 \(23 caracteres\)**  
**base 6: 3520522010102100444244423 \(25 caracteres\)**  
**base 5: 2214220303114400424121122430 \(28 caracteres\)**  
**base 4: 33333333333333333333333333333333 \(32 caracteres\)**  
**base 3: 11112220022122120101211020120210210211220 \(41 caracteres\)**  
**base 2: 1111111111111111111111111111111111111111111111111111111111111111 \(64 caracteres\)**  
**base 10: 18446744073709551615 \(20 caracteres\)**  
**base 9: 145808576354216723756 \(21 caracteres\)**  
**base 8: 1777777777777777777777 \(22 caracteres\)**  
**base 7: 45012021522523134134601 \(23 caracteres\)**  
**base 6: 3520522010102100444244423 \(25 caracteres\)**  
**base 5: 2214220303114400424121122430 \(28 caracteres\)**  
**base 4: 33333333333333333333333333333333 \(32 caracteres\)**  
**base 3: 11112220022122120101211020120210210211220 \(41 caracteres\)**  
**base 2: 1111111111111111111111111111111111111111111111111111111111111111 \(64 caracteres\)**   
## Equivalente en .NET Framework  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [\_ltoa, \_ltow](../../c-runtime-library/reference/ltoa-ltow.md)   
 [\_ltoa\_s, \_ltow\_s](../../c-runtime-library/reference/ltoa-s-ltow-s.md)   
 [\_ultoa, \_ultow](../../c-runtime-library/reference/ultoa-ultow.md)   
 [\_ultoa\_s, \_ultow\_s](../../c-runtime-library/reference/ultoa-s-ultow-s.md)