---
title: "_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l | Microsoft Docs"
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
  - "_sprintf_p"
  - "_swprintf_p_l"
  - "_swprintf_p"
  - "_sprintf_p_l"
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
  - "_sprintf_p"
  - "_swprintf_p_l"
  - "_sprintf_p_l"
  - "_swprintf_p"
  - "sprintf_p"
  - "swprint_p_l"
  - "swprintf_p"
  - "swprintf_p_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "sprintf_p_l (función)"
  - "swprintf_p (función)"
  - "swprintf_p_l (función)"
  - "_sprintf_p (función)"
  - "_sprintf_p_l (función)"
  - "_swprintf_p (función)"
  - "sprintf_p (función)"
  - "_stprintf_p (función)"
  - "stprintf_p (función)"
  - "_swprintf_p_l (función)"
  - "stprintf_p_l (función)"
  - "texto con formato [C++]"
  - "_stprintf_p_l (función)"
ms.assetid: a2ae78e8-6b0c-48d5-87a9-ea2365b0693d
caps.latest.revision: 18
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escriba los datos con formato en una cadena con la capacidad de especificar el orden en que los parámetros se utilizan en la cadena de formato.  
  
## Sintaxis  
  
```  
int _sprintf_p(  
   char *buffer,  
   size_t sizeOfBuffer,  
   const char *format [,  
   argument] ...   
);  
int _sprintf_p_l(  
   char *buffer,  
   size_t sizeOfBuffer,  
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int _swprintf_p(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   const wchar_t *format [,  
   argument]...  
);  
int _swprintf_p_l(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   const wchar_t *format,  
   locale_t locale [,  
   argument] …   
);  
```  
  
#### Parámetros  
 `buffer`  
 Ubicación de almacenamiento para los resultados  
  
 `sizeOfBuffer`  
 Número máximo de caracteres que se pueden almacenar.  
  
 `format`  
 Cadena de control de formato  
  
 `argument`  
 Argumentos opcionales  
  
 `locale`  
 Configuración regional que se va a usar.  
  
 Para obtener más información, vea [Especificaciones de formato](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## Valor devuelto  
 El número de caracteres escrito, o – 1 si se ha producido un error.  
  
## Comentarios  
 La función de `_sprintf_p` da formato y almacena una serie de caracteres y valores en `buffer`.  Cada `argument` \(si existe\) se convierte y sale según la especificación de formato correspondiente de `format`.  El formato consta de los caracteres ordinarios y tiene el mismo formato y función que el argumento de `format` para `printf_p`.  Un carácter de `NULL` se anexan después del último carácter con tipo.  Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.  La diferencia entre `_sprintf_p` y `sprintf_s` es que `_sprintf_p` admite parámetros posicionales, lo que permite especificar el orden en el que se usan los argumentos en la cadena de formato.  Para obtener más información, vea [printf\_p \(Parámetros de posición\)](../../c-runtime-library/printf-p-positional-parameters.md).  
  
 `_swprintf_p` es una versión con caracteres anchos de `_sprintf_p`; los argumentos de puntero a `_swprintf_p` son cadenas de carácter ancho.  La detección de errores de codificación en `_swprintf_p` puede diferir de la de `_sprintf_p`.  `_swprintf_p` y `fwprintf_p` se comportan exactamente igual excepto que `_swprintf_p` escribe la salida en una cadena y no en un destino de tipo `FILE` y `_swprintf_p` requiere el parámetro `count` para especificar el número máximo de caracteres que se escriban.  Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.  
  
 `_sprintf_p` devuelve el número de bytes almacenados en `buffer`, sin contar el carácter de `NULL` que finaliza.  `_swprintf_p`devuelve el número de caracteres anchos almacenados en `buffer`, sin contar el carácter ancho de `NULL` que finaliza.  Si `buffer` o `format` es un puntero NULL, o si la cadena de formato contiene caracteres de formato no válidos, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven \-1 y establecen `errno` en `EINVAL`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_stprintf_p`|`_sprintf_p`|`_sprintf_p`|`_swprintf_p`|  
|`_stprintf_p_l`|`_sprintf_p_l`|`_sprintf_p_l`|`_swprintf_p_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_sprintf_p`, `_sprintf_p_l`|\<stdio.h\>|  
|`_swprintf_p`, `_swprintf_p_l`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_sprintf_p.c  
// This program uses _sprintf_p to format various  
// data and place them in the string named buffer.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
    char     buffer[200],  
            s[] = "computer", c = 'l';  
    int      i = 35,  
            j;  
    float    fp = 1.7320534f;  
  
    // Format and print various data:   
    j  = _sprintf_p( buffer, 200,  
                     "   String:    %s\n", s );  
    j += _sprintf_p( buffer + j, 200 - j,   
                     "   Character: %c\n", c );  
    j += _sprintf_p( buffer + j, 200 - j,   
                     "   Integer:   %d\n", i );  
    j += _sprintf_p( buffer + j, 200 - j,   
                     "   Real:      %f\n", fp );  
  
    printf( "Output:\n%s\ncharacter count = %d\n",   
            buffer, j );  
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
// crt_swprintf_p.c  
// This is the wide character example which  
// also demonstrates _swprintf_p returning  
// error code.  
#include <stdio.h>  
  
#define BUFFER_SIZE 100  
  
int main( void )  
{  
    wchar_t buffer[BUFFER_SIZE];  
    int     len;  
  
    len = _swprintf_p(buffer, BUFFER_SIZE, L"%2$s %1$d",  
                      0, L" marbles in your head.");  
    _printf_p( "Wrote %d characters\n", len );  
  
    // _swprintf_p fails because string contains WEOF (\xffff)  
    len = _swprintf_p(buffer, BUFFER_SIZE, L"%s",   
                      L"Hello\xffff world" );  
    _printf_p( "Wrote %d characters\n", len );  
}  
```  
  
  **Escribió 24 caracteres**  
**Escribió \-1 caracteres**   
## Equivalente en .NET Framework  
 [System::String::Format](https://msdn.microsoft.com/en-us/library/system.string.format.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [\_fprintf\_p, \_fprintf\_p\_l, \_fwprintf\_p, \_fwprintf\_p\_l](../../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)   
 [fprintf, \_fprintf\_l, fwprintf, \_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [\_printf\_p, \_printf\_p\_l, \_wprintf\_p, \_wprintf\_p\_l](../../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)   
 [printf, \_printf\_l, wprintf, \_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf, \_scanf\_l, wscanf, \_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf, \_sscanf\_l, swscanf, \_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [sscanf\_s, \_sscanf\_s\_l, swscanf\_s, \_swscanf\_s\_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)   
 [vprintf \(Funciones\)](../../c-runtime-library/vprintf-functions.md)   
 [printf\_p \(Parámetros de posición\)](../../c-runtime-library/printf-p-positional-parameters.md)