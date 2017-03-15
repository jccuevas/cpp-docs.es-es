---
title: "strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "strncpy"
  - "_strncpy_l"
  - "_mbsncpy"
  - "wcsncpy"
  - "_mbsncpy_l"
  - "_wcsncpy_l"
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
  - "_fstrncpy"
  - "strncpy"
  - "_ftcsncpy"
  - "_tcsnccpy_l"
  - "_tcsnccpy"
  - "_mbsncpy"
  - "wcsncpy"
  - "_tcsncpy"
  - "_strncpy_l"
  - "_mbsncpy_l"
  - "_wcsncpy_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fstrncpy (función)"
  - "_ftcsncpy (función)"
  - "_mbsncpy (función)"
  - "_mbsncpy_l (función)"
  - "_strncpy_l (función)"
  - "_tcsnccpy (función)"
  - "_tcsnccpy_l (función)"
  - "_tcsncpy (función)"
  - "_tcsncpy_l (función)"
  - "_wcsncpy_l (función)"
  - "caracteres [C++], copiar"
  - "copiar caracteres de cadenas"
  - "fstrncpy (función)"
  - "ftcsncpy (función)"
  - "mbsncpy (función)"
  - "mbsncpy_l (función)"
  - "cadenas [C++], copiar"
  - "strncpy (función)"
  - "strncpy_l (función)"
  - "tcsnccpy (función)"
  - "tcsnccpy_l (función)"
  - "tcsncpy (función)"
  - "tcsncpy_l (función)"
  - "wcsncpy (función)"
  - "wcsncpy_l (función)"
ms.assetid: ac4345a1-a129-4f2f-bb8a-373ec58ab8b0
caps.latest.revision: 42
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 42
---
# strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Copie los caracteres de una cadena en otra.  Existen versiones más seguras de estas funciones; vea [strncpy\_s, \_strncpy\_s\_l, wcsncpy\_s, \_wcsncpy\_s\_l, \_mbsncpy\_s, \_mbsncpy\_s\_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md).  
  
> [!IMPORTANT]
>  `_mbsncpy` y `_mbsncpy_l` no se pueden usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
char *strncpy(  
   char *strDest,  
   const char *strSource,  
   size_t count   
);  
char *_strncpy_l(  
   char *strDest,  
   const char *strSource,  
   size_t count,  
   locale_t locale   
);  
wchar_t *wcsncpy(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count   
);  
wchar_t *_wcsncpy_l(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count,  
   locale_t locale   
);  
unsigned char *_mbsncpy(  
   unsigned char *strDest,  
   const unsigned char *strSource,  
   size_t count   
);  
unsigned char *_mbsncpy_l(  
   unsigned char *strDest,  
   const unsigned char *strSource,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
char *strncpy(  
   char (&strDest)[size],  
   const char *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
char *_strncpy_l(  
   char (&strDest)[size],  
   const char *strSource,  
   size_t count,  
   locale_t locale   
); // C++ only  
template <size_t size>  
wchar_t *wcsncpy(  
   wchar_t (&strDest)[size],  
   const wchar_t *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
wchar_t *_wcsncpy_l(  
   wchar_t (&strDest)[size],  
   const wchar_t *strSource,  
   size_t count,  
   locale_t locale   
); // C++ only  
template <size_t size>  
unsigned char *_mbsncpy(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
unsigned char *_mbsncpy_l(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### Parámetros  
 `strDest`  
 Cadena de destino.  
  
 `strSource`  
 Cadena de origen.  
  
 `count`  
 Número de caracteres que se van a copiar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Devuelve `strDest`.  No se reserva ningún valor devuelto para indicar un error.  
  
## Comentarios  
 La función `strncpy` copia los primeros `count` caracteres de `strSource` en `strDest` y devuelve `strDest`.  Si `count` es menor o igual que la longitud de `strSource`, no se anexa ningún carácter nulo automáticamente a la cadena copiada.  Si `count` es mayor que la longitud de `strSource`, a cadena de destino se completa con caracteres nulos hasta la longitud `count`.  El comportamiento de `strncpy` no se define si las cadenas de origen y de destino se superponen.  
  
> [!IMPORTANT]
>  `strncpy` no comprueba si hay espacio suficiente en `strDest`, lo que la convierte en una posible causa de saturaciones del búfer.  El argumento `count` limita el número de caracteres que se copian, no el tamaño de `strDest`.  Vea el ejemplo siguiente.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
 Si `strDest` o `strSource` es un puntero `NULL`, o si `count` es menor o igual que cero, se invoca el controlador de parámetros no válidos, tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven \-1 y establecen `errno` en `EINVAL`.  
  
 `wcsncpy` y `_mbsncpy` son versiones de caracteres anchos y multibyte de `strncpy`.  Los argumentos y el valor devuelto de `wcsncpy` y `_mbsncpy` varían en consecuencia.  Por lo demás, estas seis funciones se comportan exactamente igual.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan la configuración regional pasada en lugar de la configuración regional de su comportamiento dependiente de la configuración regional.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 En C\+\+, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsncpy`|`strncpy`|`_mbsnbcpy`|`wcsncpy`|  
|`_tcsncpy_l`|`_strncpy_l`|`_mbsnbcpy_l`|`_wcsncpy_l`|  
  
> [!NOTE]
>  `_strncpy_l` y `_wcsncpy_l` no dependen de la configuración regional; se proporcionan solo para `_tcsncpy_l` y no se han diseñado para recibir llamadas directamente.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strncpy`|\<string.h\>|  
|`wcsncpy`|\<string.h\> o \<wchar.h\>|  
|`_mbsncpy`, `_mbsncpy_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad de plataformas, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de `strncpy` y cómo su uso incorrecto puede provocar errores de programa y problemas de seguridad.  El compilador genera una advertencia para cada llamada a `strncpy` similar a **crt\_strncpy\_x86.c\(15\) : warning C4996: 'strncpy': This function or variable may be unsafe. Consider using strncpy\_s instead. To disable deprecation, use \_CRT\_SECURE\_NO\_WARNINGS. See online help for details.**  
  
```  
// crt_strncpy_x86.c  
// Use this command in an x86 developer command prompt to compile:   
// cl /TC /W3 crt_strncpy_x86.c  
  
#include <stdio.h>  
#include <string.h>  
  
int main() {  
   char t[20];  
   char s[20];  
   char *p = 0, *q = 0;  
  
   strcpy_s(s, sizeof(s), "AA BB CC");  
   // Note: strncpy is deprecated; consider using strncpy_s instead  
   strncpy(s, "aa", 2);     // "aa BB CC"         C4996  
   strncpy(s + 3, "bb", 2); // "aa bb CC"         C4996  
   strncpy(s, "ZZ", 3);     // "ZZ",              C4996  
                            // count greater than strSource, null added  
   printf("%s\n", s);  
  
   strcpy_s(s, sizeof(s), "AA BB CC");  
   p = strstr(s, "BB");  
   q = strstr(s, "CC");  
   strncpy(s, "aa", p - s - 1);   // "aa BB CC"   C4996  
   strncpy(p, "bb", q - p - 1);   // "aa bb CC"   C4996  
   strncpy(q, "cc",  q - s);      // "aa bb cc"   C4996  
   strncpy(q, "dd", strlen(q));   // "aa bb dd"   C4996  
   printf("%s\n", s);  
  
   // some problems with strncpy  
   strcpy_s(s, sizeof(s), "test");  
   strncpy(t, "this is a very long string", 20 ); // C4996  
   // Danger: at this point, t has no terminating null,  
   // so the printf continues until it runs into one.  
   // In this case, it will print "this is a very long test"  
   printf("%s\n", t);  
  
   strcpy_s(t, sizeof(t), "dogs like cats");  
   printf("%s\n", t);  
  
   strncpy(t + 10, "to chase cars.", 14); // C4996  
   printf("%s\n", t);  
  
   // strncpy has caused a buffer overrun and corrupted string s  
   printf("Buffer overrun: s = '%s' (should be 'test')\n", s);  
   // Since the stack grows from higher to lower addresses, buffer  
   // overruns can corrupt function return addresses on the stack,  
   // which can be exploited to run arbitrary code.  
}  
```  
  
 Salida  
  
  **ZZ**  
**aa bb dd**  
**this is a very long test**  
**dogs like cats**  
**dogs like to chase cars.  Saturación del búfer: s \= 'ars.' \(debe ser 'test'\)**  El diseño de las variables automáticas y el nivel de detección de errores y protección del código pueden variar con la configuración de compilador modificada.  Este ejemplo puede tener resultados diferentes si se crea en otros entornos de compilación o con otras opciones del compilador.  
  
## Equivalente en .NET Framework  
 [System::String::Copy](https://msdn.microsoft.com/en-us/library/system.string.copy.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbsnbcpy, \_mbsnbcpy\_l](../../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md)   
 [strcat, wcscat, \_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp, wcscmp, \_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy, wcscpy, \_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncat, \_strncat\_l, wcsncat, \_wcsncat\_l, \_mbsncat, \_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp, wcsncmp, \_mbsncmp, \_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [\_strnicmp, \_wcsnicmp, \_mbsnicmp, \_strnicmp\_l, \_wcsnicmp\_l, \_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr, wcsrchr, \_mbsrchr, \_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [\_strset, \_strset\_l, \_wcsset, \_wcsset\_l, \_mbsset, \_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn, wcsspn, \_mbsspn, \_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)   
 [strncpy\_s, \_strncpy\_s\_l, wcsncpy\_s, \_wcsncpy\_s\_l, \_mbsncpy\_s, \_mbsncpy\_s\_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)   
 [strcpy\_s, wcscpy\_s, \_mbscpy\_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)