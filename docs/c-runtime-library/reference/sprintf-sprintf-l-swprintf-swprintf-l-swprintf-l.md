---
title: "sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__swprintf_l"
  - "sprintf"
  - "_sprintf_l"
  - "_swprintf_l"
  - "swprintf"
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
  - "ntdll.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_stprintf_l"
  - "__swprintf_l"
  - "sprintf_l"
  - "swprintf"
  - "_sprintf_l"
  - "sprintf"
  - "_stprintf"
  - "stprintf_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__swprintf_l (función)"
  - "_CRT_NON_CONFORMING_SWPRINTFS"
  - "_sprintf_l (función)"
  - "_stprintf (función)"
  - "_stprintf_l (función)"
  - "_swprintf_l (función)"
  - "texto con formato [C++]"
  - "sprintf (función)"
  - "sprintf_l (función)"
  - "stprintf (función)"
  - "stprintf_l (función)"
  - "cadenas [C++], escribir"
  - "swprintf (función)"
  - "swprintf_l (función)"
ms.assetid: f6efe66f-3563-4c74-9455-5411ed939b81
caps.latest.revision: 36
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 36
---
# sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escribir datos con formato en una cadena.  Hay disponibles versiones más seguras de algunas de estas funciones; vea [sprintf\_s, \_sprintf\_s\_l, swprintf\_s, \_swprintf\_s\_l](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md).  Las versiones seguras de `swprintf` y `_swprintf_l` no aceptan un parámetro `count`.  
  
## Sintaxis  
  
```  
int sprintf(  
   char *buffer,  
   const char *format [,  
   argument] ...   
);  
int _sprintf_l(  
   char *buffer,  
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int swprintf(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format [,  
   argument]...  
);  
int _swprintf_l(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
);  
int __swprintf_l(  
   wchar_t *buffer,  
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
);  
template <size_t size>  
int sprintf(  
   char (&buffer)[size],  
   const char *format [,  
   argument] ...   
); // C++ only  
template <size_t size>  
int _sprintf_l(  
   char (&buffer)[size],  
   const char *format,  
   locale_t locale [,  
   argument] ...   
); // C++ only  
  
```  
  
#### Parámetros  
 `buffer`  
 Ubicación de almacenamiento para los resultados  
  
 `count`  
 Número máximo de caracteres que se van a almacenar en la versión Unicode de esta función.  
  
 `format`  
 Cadena de control de formato  
  
 `argument`  
 Argumentos opcionales  
  
 `locale`  
 Configuración regional que se va a usar.  
  
 Para obtener más información, vea [Especificaciones de formato](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## Valor devuelto  
 El número de caracteres escrito, o – 1 si se ha producido un error.  Si `buffer` o `format` es un puntero nulo, se invoca el controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven \-1 y establecen `errno` en `EINVAL`.  
  
 `sprintf` devuelve el número de bytes almacenados en `buffer`, sin contar el carácter null de terminación.  `swprintf` devuelve el número de caracteres anchos almacenados en `buffer`, sin contar el carácter ancho null de terminación.  
  
## Comentarios  
 La función `sprintf` da formato y almacena una serie de caracteres y valores en `buffer`.  Cada `argument` \(si existe\) se convierte y sale según la especificación de formato correspondiente de `format`.  El formato consta de caracteres ordinarios y tiene el mismo formato y función que el argumento `format` para [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md).  Un carácter null se anexa después del último carácter escrito.  Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.  
  
> [!IMPORTANT]
>  Al usar `sprintf`, no hay forma de limitar el número de caracteres escritos, lo que significa que el código que use `sprintf` está expuesto a saturaciones del búfer.  Considere la posibilidad de usar la función relacionada [\_snprintf](../../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md), que especifica un número máximo de caracteres que se escribirá en `buffer`, o bien, use [\_scprintf](../../c-runtime-library/reference/scprintf-scprintf-l-scwprintf-scwprintf-l.md) para determinar el tamaño que requiere un búfer.  Además, asegúrese de que `format` no es una cadena definida por el usuario.  
  
 `swprintf` es una versión con caracteres anchos de `sprintf`; los argumentos de puntero a `swprintf` son cadenas de carácter ancho.  La detección de errores de codificación en `swprintf` puede diferir de la de `sprintf`.  `swprintf` y `fwprintf` se comportan exactamente igual, salvo por el hecho de que `swprintf` escribe la salida en una cadena y no en un destino de tipo `FILE`, y `swprintf` requiere el parámetro `count` para especificar el número máximo de caracteres que se escribirán.  Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.  
  
 `swprintf` se ajusta a ISO C estándar, que requiere el segundo parámetro, `count`, de tipo `size_t`.  Para imponer el anterior comportamiento no estándar, defina `_CRT_NON_CONFORMING_SWPRINTFS`.  Es posible que el comportamiento anterior se quite en una versión futura, por lo que el código se debe cambiar de forma para que use el nuevo comportamiento estándar.  
  
 En C\+\+, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_stprintf`|`sprintf`|`sprintf`|`_swprintf`|  
|`_stprintf_l`|`_sprintf_l`|`_sprintf_l`|`__swprintf_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`sprintf`, `_sprintf_l`|\<stdio.h\>|  
|`swprintf`, `_swprintf_l`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_sprintf.c  
// compile with: /W3  
// This program uses sprintf to format various  
// data and place them in the string named buffer.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char  buffer[200], s[] = "computer", c = 'l';  
   int   i = 35, j;  
   float fp = 1.7320534f;  
  
   // Format and print various data:   
   j  = sprintf( buffer,     "   String:    %s\n", s ); // C4996  
   j += sprintf( buffer + j, "   Character: %c\n", c ); // C4996  
   j += sprintf( buffer + j, "   Integer:   %d\n", i ); // C4996  
   j += sprintf( buffer + j, "   Real:      %f\n", fp );// C4996  
   // Note: sprintf is deprecated; consider using sprintf_s instead  
  
   printf( "Output:\n%s\ncharacter count = %d\n", buffer, j );  
}  
```  
  
  **Resultado:**  
 **Cadena: equipo**  
 **Carácter: l**  
 **Entero: 35**  
 **Real: 1,732053**  
**Recuento de caracteres \= 79**   
## Ejemplo  
  
```  
// crt_swprintf.c  
// wide character example  
// also demonstrates swprintf returning error code  
#include <stdio.h>  
  
int main( void )  
{  
   wchar_t buf[100];  
   int len = swprintf( buf, 100, L"%s", L"Hello world" );  
   printf( "wrote %d characters\n", len );  
   len = swprintf( buf, 100, L"%s", L"Hello\xffff world" );  
   // swprintf fails because string contains WEOF (\xffff)  
   printf( "wrote %d characters\n", len );  
}  
```  
  
  **escribió 11 caracteres**  
**escribió \-1 caracteres**   
## Equivalente en .NET Framework  
 [System::String::Format](https://msdn.microsoft.com/en-us/library/system.string.format.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fprintf, \_fprintf\_l, fwprintf, \_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, \_printf\_l, wprintf, \_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf, \_scanf\_l, wscanf, \_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf, \_sscanf\_l, swscanf, \_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [vprintf \(Funciones\)](../../c-runtime-library/vprintf-functions.md)