---
title: "_ltoa, _ltow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ltoa"
  - "_ltow"
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
  - "ltow"
  - "_ltot"
  - "_ltoa"
  - "_ltow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ltoa (función)"
  - "_ltow (función)"
  - "convertir enteros"
  - "convertir números, a cadenas"
  - "conversión de entero largo a cadena"
  - "ltoa (función)"
  - "ltow (función)"
ms.assetid: 14036104-2c25-4759-87c0-918ed8521e47
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _ltoa, _ltow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte un entero largo en una cadena.  Hay disponibles versiones más seguras de estas funciones; vea [\_ltoa\_s, \_ltow\_s](../../c-runtime-library/reference/ltoa-s-ltow-s.md).  
  
## Sintaxis  
  
```  
char *_ltoa(  
   long value,  
   char *str,  
   int radix   
);  
wchar_t *_ltow(  
   long value,  
   wchar_t *str,  
   int radix   
);  
template <size_t size>  
char *_ltoa(  
   long value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t *_ltow(  
   long value,  
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
 Base de `value`.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve un puntero a `str`.  No se devuelve ningún error.  
  
## Comentarios  
 La función de `_ltoa` convierte los dígitos de `value` en una cadena de caracteres terminada en null y almacena el resultado \(hasta 33 bytes\) en `str`.  El argumento de `radix` especifica la base de `value`, que debe estar en el intervalo comprendido entre 2 y 36.  Si `radix` es igual a 10 y `value` es negativo, el primer carácter de la cadena almacenada es el signo menos \(–\).  `_ltow` es una versión con caracteres anchos de `_ltoa`; el segundo argumento y el valor devuelto de `_ltow` son cadenas de caracteres.  Cada una de estas funciones es Microsoft\- concreto.  
  
> [!IMPORTANT]
>  Para evitar las saturaciones del búfer, asegúrese de que el búfer de `str` tiene el tamaño suficiente para contener los dígitos convertidos más el carácter nulo final y un carácter de signo.  
  
 En C\+\+, estas funciones tienen sobrecargas de plantilla.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_ltot`|`_ltoa`|`_ltoa`|`_ltow`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_ltoa`|\<stdlib.h\>|  
|`_ltow`|\<stdlib.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea el ejemplo para [\_itoa](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md).  
  
## Equivalente en .NET Framework  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [\_itoa, \_i64toa, \_ui64toa, \_itow, \_i64tow, \_ui64tow](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)   
 [\_ultoa, \_ultow](../../c-runtime-library/reference/ultoa-ultow.md)