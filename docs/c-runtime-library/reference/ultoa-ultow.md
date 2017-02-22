---
title: "_ultoa, _ultow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ultoa"
  - "_ultow"
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
  - "ultot"
  - "ultow"
  - "_ultoa"
  - "_ultow"
  - "_ultot"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ultoa (función)"
  - "_ultot (función)"
  - "_ultow (función)"
  - "convertir enteros"
  - "convertir números, a cadenas"
  - "enteros, convertir"
  - "ultot (función)"
  - "ultow (función)"
ms.assetid: 7a472dc4-5652-4513-93c3-3358522c23be
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _ultoa, _ultow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte un entero unsigned long en una cadena.  Hay disponibles versiones más seguras de estas funciones; vea [\_ultoa\_s, \_ultow\_s](../../c-runtime-library/reference/ultoa-s-ultow-s.md).  
  
## Sintaxis  
  
```  
char *_ultoa(  
   unsigned long value,  
   char *str,  
   int radix   
);  
wchar_t *_ultow(  
   unsigned long value,  
   wchar_t *str,  
   int radix   
);  
template <size_t size>  
char *_ultoa(  
   unsigned long value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t *_ultow(  
   unsigned long value,  
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
 Base de *`value`.*  
  
## Valor devuelto  
 Cada una de estas funciones devuelve un puntero a `str`.  No se devuelve ningún error.  
  
## Comentarios  
 La función de `_ultoa` convierte `value` en una cadena de caracteres terminada en null y almacena el resultado \(hasta 33 bytes\) en `str`.  No se realiza el ningún la comprobación de desbordamiento.  `radix` especifica la base de `value`; `radix` debe estar en el intervalo de 2 a 36.  `_ultow` es una versión con caracteres anchos de `_ultoa`.  
  
> [!IMPORTANT]
>  Para evitar las saturaciones del búfer, asegúrese de que el búfer de `str` es bastante grande para contener los dígitos convertidos más el nulo\- carácter final.  
  
 En C\+\+, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_ultot`|`_ultoa`|`_ultoa`|`_ultow`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_ultoa`|\<stdlib.h\>|  
|`_ultow`|\<stdlib.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea el ejemplo para [\_itoa](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md).  
  
## Equivalente en .NET Framework  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [\_itoa, \_i64toa, \_ui64toa, \_itow, \_i64tow, \_ui64tow](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)