---
title: "_ltoa_s, _ltow_s | Microsoft Docs"
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
  - "_ltoa_s"
  - "_ltow_s"
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
apitype: "DLLExport"
f1_keywords: 
  - "_ltow_s"
  - "_ltoa_s"
  - "ltoa_s"
  - "ltow_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ltoa_s (función)"
  - "_ltow_s (función)"
  - "convertir enteros"
  - "convertir números, a cadenas"
  - "conversión de entero largo a cadena"
  - "ltoa_s (función)"
  - "ltow_s (función)"
ms.assetid: d7dc61ea-1ccd-412d-b262-555a58647386
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ltoa_s, _ltow_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte un entero largo en una cadena.  Estas versiones de [\_ltoa, \_ltow](../../c-runtime-library/reference/ltoa-ltow.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t _ltoa_s(  
    long value,  
    char *str,  
    size_t sizeOfstr,  
    int radix   
);  
errno_t _ltow_s(  
    long value,  
    wchar_t *str,  
    size_t sizeOfstr,  
    int radix   
);  
template <size_t size>  
errno_t _ltoa_s(  
    long value,  
    char (&str)[size],  
    int radix   
); // C++ only  
template <size_t size>  
errno_t _ltow_s(  
    long value,  
    wchar_t (&str)[size],  
    int radix   
); // C++ only  
```  
  
#### Parámetros  
 `value`  
 Número que se va a convertir.  
  
 `str`  
 Búfer para la cadena resultante.  
  
 `sizeOfstr`  
 Tamaño de `str` en bytes para `_ltoa_s` o palabras para `_ltow_s`.  
  
 `radix`  
 Base de `value`.  
  
## Valor devuelto  
 Cero si la función es correcta o un código de error.  
  
## Comentarios  
 La función de `_ltoa_s` convierte los dígitos de `value` en una cadena de caracteres terminada en null y almacena el resultado \(hasta 33 bytes\) en `str`.  El argumento de `radix` especifica la base de `value`, que debe estar en el intervalo comprendido entre 2 y 36.  Si `radix` es igual a 10 y `value` es negativo, el primer carácter de la cadena almacenada es el signo menos \(–\).  `_ltow_s` es una versión con caracteres anchos de `_ltoa_s`; el segundo argumento de `_ltow_s` es las cadenas de caracteres anchos.  
  
 Si `str` es un puntero de `NULL` o `sizeOfstr` es menor o igual que cero, estas funciones se invoca un controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven \-1 y `errno` establecido en `EINVAL` o si `value` o `str` fuera del intervalo de un entero largo, estas funciones devuelve \-1 y establece `errno` a `ERANGE`.  
  
 En C\+\+, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer \(lo que elimina la necesidad de especificar un argumento de tamaño\) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_ltot_s`|`_ltoa_s`|`_ltoa_s`|`_ltow_s`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_ltoa_s`|\<stdlib.h\>|  
|`_ltow_s`|\<stdlib.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [\_itoa, \_i64toa, \_ui64toa, \_itow, \_i64tow, \_ui64tow](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)   
 [\_ultoa, \_ultow](../../c-runtime-library/reference/ultoa-ultow.md)   
 [\_ultoa\_s, \_ultow\_s](../../c-runtime-library/reference/ultoa-s-ultow-s.md)