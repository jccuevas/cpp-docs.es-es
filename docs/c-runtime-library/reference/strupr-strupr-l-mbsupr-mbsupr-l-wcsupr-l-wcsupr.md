---
title: "_strupr, _strupr_l, _mbsupr, _mbsupr_l, _wcsupr_l, _wcsupr | Microsoft Docs"
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
  - "_mbsupr_l"
  - "_mbsupr"
  - "_strupr_l"
  - "_wcsupr"
  - "_wcsupr_l"
  - "_strupr"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_mbsupr"
  - "_ftcsupr"
  - "mbsupr"
  - "_tcsupr"
  - "strupr_l"
  - "_fstrupr"
  - "_strupr"
  - "mbsupr_l"
  - "_wcsupr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fstrupr (función)"
  - "_ftcsupr (función)"
  - "_mbsupr (función)"
  - "_mbsupr_l (función)"
  - "_strupr (función)"
  - "_strupr_l (función)"
  - "_tcsupr (función)"
  - "_tcsupr_l (función)"
  - "_wcsupr (función)"
  - "_wcsupr_l (función)"
  - "convertir mayúsculas y minúsculas, CRT (funciones)"
  - "fstrupr (función)"
  - "ftcsupr (función)"
  - "mbsupr (función)"
  - "mbsupr_l (función)"
  - "conversión de cadenas [C++], mayúsculas y minúsculas"
  - "cadenas [C++], mayúsculas y minúsculas"
  - "cadenas [C++], convertir mayúsculas y minúsculas"
  - "strupr (función)"
  - "strupr_l (función)"
  - "tcsupr (función)"
  - "tcsupr_l (función)"
  - "mayúsculas, convertir cadenas en"
  - "wcsupr (función)"
  - "wcsupr_l (función)"
ms.assetid: caac8f16-c233-41b6-91ce-575ec7061b77
caps.latest.revision: 26
caps.handback.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strupr, _strupr_l, _mbsupr, _mbsupr_l, _wcsupr_l, _wcsupr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cambia la cadena a mayúsculas.  Hay disponibles versiones más seguras de estas funciones; vea [\_strupr\_s, \_strupr\_s\_l, \_mbsupr\_s, \_mbsupr\_s\_l, \_wcsupr\_s, \_wcsupr\_s\_l](../../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md).  
  
> [!IMPORTANT]
>  `_mbsupr` y `_mbsupr_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
char *_strupr(  
   char *str   
);  
wchar_t *_wcsupr(  
   wchar_t *str   
);  
unsigned char *_mbsupr(  
   unsigned char *str   
);  
char *_strupr_l(  
   char *str,  
   _locale_t locale  
);  
wchar_t *_wcsupr_l(  
   wchar_t *str,  
   _locale_t locale  
);  
unsigned char *_mbsupr_l(  
   unsigned char *str,  
   _locale_t locale  
);  
template <size_t size>  
char *_strupr(  
   char (&str)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_wcsupr(  
   wchar_t (&str)[size]  
); // C++ only  
template <size_t size>  
unsigned char *_mbsupr(  
   unsigned char (&str)[size]  
); // C++ only  
template <size_t size>  
char *_strupr_l(  
   char (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
wchar_t *_wcsupr_l(  
   wchar_t (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
unsigned char *_mbsupr_l(  
   unsigned char (&str)[size],  
   _locale_t locale  
); // C++ only  
```  
  
#### Parámetros  
 `str`  
 Cadena que se va a poner en mayúsculas.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Devuelve un puntero a la cadena modificada.  Dado que la modificación se hace en contexto, el puntero devuelto es el mismo que el puntero que se pasa como argumento de entrada.  No se reserva ningún valor devuelto para indicar un error.  
  
## Comentarios  
 La función `_strupr` convierte, en su sitio, cada minúscula de `str` en mayúscula.  El valor de la categoría `LC_CTYPE` de la configuración regional determina la conversión.  Otros caracteres no resultan afectados.  Para obtener más información sobre `LC_CTYPE`, vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual; las versiones con el sufijo `_l` son idénticas salvo que usan el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 `_wcsupr` y `_mbsupr` son versiones de caracteres anchos y multibyte de `_strupr`.  El argumento y el valor devuelto de `_wcsupr` son cadenas de caracteres anchos; los de `_mbsupr` son cadenas de caracteres multibyte.  Estas tres funciones se comportan exactamente igual.  
  
 Si `str` es un puntero nulo, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven la cadena original y establecen `errno` en `EINVAL`.  
  
 En C\+\+, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsupr`|`_strupr`|`_mbsupr`|`_wcsupr`|  
|`_tcsupr_l`|`_strupr_l`|`_mbsupr_l`|`_wcsupr_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_strupr`, `_strupr_l`|\<string.h\>|  
|`_wcsupr`, `_wcsupr_l`|\<string.h\> o \<wchar.h\>|  
|`_mbsupr`, `_mbsupr_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
 Vea el ejemplo de [\_strlwr](../../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md).  
  
## Equivalente en .NET Framework  
 [System::String::ToUpper](https://msdn.microsoft.com/en-us/library/system.string.toupper.aspx)  
  
## Vea también  
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [\_strlwr, \_wcslwr, \_mbslwr, \_strlwr\_l, \_wcslwr\_l, \_mbslwr\_l](../../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md)