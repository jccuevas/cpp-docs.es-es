---
title: "snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l | Microsoft Docs"
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
  - "_snwprintf"
  - "_snprintf"
  - "_snprintf_l"
  - "_snwprintf_l"
  - "snprintf"
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
  - "_snprintf"
  - "snprintf_l"
  - "snwprintf_l"
  - "sntprintf"
  - "snprintf"
  - "_sntprintf"
  - "_sntprintf_l"
  - "sntprintf_l"
  - "snwprintf"
  - "_snprintf_l"
  - "_snwprintf"
  - "_snwprintf_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "snwprintf_l (función)"
  - "sntprintf_l (función)"
  - "snprintf_l (función)"
  - "_snwprintf_l (función)"
  - "_sntprintf_l (función)"
  - "_snwprintf (función)"
  - "_snprintf (función)"
  - "_sntprintf (función)"
  - "_snprintf_l (función)"
  - "snwprintf (función)"
  - "snprintf (función)"
  - "sntprintf (función)"
  - "texto con formato [C++]"
ms.assetid: 5976c9c8-876e-4ac9-a515-39f3f7fd0925
caps.latest.revision: 35
caps.handback.revision: 35
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escribe datos con formato en una cadena. Hay versiones más seguras de estas funciones disponibles; vea [\_snprintf\_s, \_snprintf\_s\_l, \_snwprintf\_s, \_snwprintf\_s\_l](../../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md).  
  
## Sintaxis  
  
```  
int snprintf(  
   char *buffer,  
   size_t count,  
   const char *format [,  
   argument] ...   
);  
int _snprintf(  
   char *buffer,  
   size_t count,  
   const char *format [,  
   argument] ...   
);  
int _snprintf_l(  
   char *buffer,  
   size_t count,  
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int _snwprintf(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format [,  
   argument] ...   
);  
int _snwprintf_l(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
);  
template <size_t size>  
int _snprintf(  
   char (&buffer)[size],  
   size_t count,  
   const char *format [,  
   argument] ...   
); // C++ only  
template <size_t size>  
int _snprintf_l(  
   char (&buffer)[size],  
   size_t count,  
   const char *format,  
   locale_t locale [,  
   argument] ...   
); // C++ only  
template <size_t size>  
int _snwprintf(  
   wchar_t (&buffer)[size],  
   size_t count,  
   const wchar_t *format [,  
   argument] ...   
); // C++ only  
template <size_t size>  
int _snwprintf_l(  
   wchar_t (&buffer)[size],  
   size_t count,  
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
); // C++ only  
```  
  
#### Parámetros  
 `buffer`  
 Ubicación de almacenamiento del resultado.  
  
 `count`  
 Número máximo de caracteres que se pueden almacenar.  
  
 `format`  
 Cadena de control de formato.  
  
 `argument`  
 Argumentos opcionales.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
 Para obtener más información, consulta [Sintaxis de especificación de formato: Funciones printf y wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## Valor devuelto  
 Deje que `len` sea la longitud de la cadena de datos con formato, sin incluir el carácter null final.`len` y `count` se especifican en bytes para `snprintf` y `_snprintf`, y en caracteres anchos para `_snwprintf`.  
  
 Para todas las funciones, si `len` \< `count`, se almacenan `len` caracteres en `buffer`, se anexa un terminador null y se devuelve `len`.  
  
 La función `snprintf` trunca el resultado cuando `len` es mayor o igual que `count`, y coloca un terminador null en `buffer[count-1]`. El valor devuelto es `len`, el número de caracteres que habrían resultado si `count` hubiese sido lo suficientemente grande. La función `snprintf` devuelve un valor negativo si se produce un error de codificación.  
  
 Para todas las funciones distintas de `snprintf`, si `len` \= `count`, se almacenan `len` caracteres en `buffer`, no se anexa ningún terminador null y se devuelve `len`. Si `len` \> `count`, se almacenan `count` caracteres en `buffer`, no se anexa ningún terminador null y se devuelve un valor negativo.  
  
 Si `buffer` es un puntero null y `count` es cero, se devuelve `len` como el número de caracteres necesarios para dar formato al resultado, sin incluir el carácter null final. Para realizar una llamada correcta con los mismos parámetros `argument` y `locale`, asigne un búfer que contenga al menos `len` \+ 1 caracteres.  
  
 Si `buffer` es un puntero null y `count` es distinto de cero, o si `format` es un puntero null, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven \-1 y establecen `errno` en `EINVAL`.  
  
 Para obtener más información sobre estos y otros códigos de error, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función `snprintf` y la familia de funciones `_snprintf` dan formato y almacenan `count` caracteres o menos en `buffer`. La función `snprintf` siempre almacena un carácter null final y trunca el resultado si es necesario. La familia de funciones `_snprintf` solo anexa un carácter null final si la longitud de la cadena con formato es estrictamente menor que `count` caracteres. Cada `argument` \(si existe\) se convierte y se muestra según la especificación de formato correspondiente de `format`. El formato consta de caracteres ordinarios y tiene el mismo formato y función que el argumento `format` para [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md). Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.  
  
> [!IMPORTANT]
>  Asegúrese de que `format` no es una cadena definida por el usuario. Puesto que las funciones `_snprintf` no garantizan la finalización en NULL, en concreto cuando el valor devuelto es `count`, hay que asegurarse de que vayan seguidas de código que agregue el terminador null. Para obtener más información, vea [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) \(Evitar saturaciones del búfer\).  
  
 A partir del UCRT en Visual Studio 2015 y Windows 10, la palabra clave `snprintf` ya no es idéntica a `_snprintf`. El comportamiento de la función `snprintf` es ahora compatible con el estándar C99.  
  
 `_snwprintf` es una versión con caracteres anchos de `_snprintf`; los argumentos de puntero a `_snwprintf` son cadenas de carácter ancho. La detección de errores de codificación en `_snwprintf` puede diferir de la de `_snprintf`.`_snwprintf`, como `swprintf`, escribe el resultado en una cadena en lugar de hacerlo en un destino de tipo `FILE`.  
  
 Las versiones de estas funciones que tienen el sufijo `_l` son idénticas salvo que usan el parámetro de configuración regional que se pasa en lugar de la configuración regional del subproceso actual.  
  
 En C\+\+, estas funciones tienen sobrecargas de plantilla que invocan sus homólogos más seguros y más recientes. Para obtener más información, consulta [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_sntprintf`|`_snprintf`|`_snprintf`|`_snwprintf`|  
|`_sntprintf_l`|`_snprintf_l`|`_snprintf_l`|`_snwprintf_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`snprintf`, `_snprintf`,  `_snprintf_l`|\<stdio.h\>|  
|`_snwprintf`, `_snwprintf_l`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```c  
// crt_snprintf.c  
// compile with: /W3  
#include <stdio.h>  
#include <stdlib.h>  
  
#if !defined(__cplusplus)  
typedef int bool;  
const bool true = 1;  
const bool false = 0;  
#endif  
  
#define FAIL 0 // change to 1 and see what happens  
  
int main(void)  
{  
   char buffer[200];  
   const static char s[] = "computer"  
#if FAIL  
"computercomputercomputercomputercomputercomputercomputercomputer"  
"computercomputercomputercomputercomputercomputercomputercomputer"  
"computercomputercomputercomputercomputercomputercomputercomputer"  
"computercomputercomputercomputercomputercomputercomputercomputer"  
#endif  
   ;  
   const char c = 'l';   
   const int i = 35;  
#if FAIL  
   const double fp = 1e300; // doesn't fit in the buffer  
#else  
   const double fp = 1.7320534;  
#endif  
   /* !subtract one to prevent "squeezing out" the terminal nul! */  
   const int bufferSize = sizeof(buffer)/sizeof(buffer[0]) - 1;  
   int bufferUsed = 0;  
   int bufferLeft = bufferSize - bufferUsed;  
   bool bSuccess = true;  
   buffer[0] = 0;  
  
   /* Format and print various data: */  
  
   if (bufferLeft > 0)  
   {  
      int perElementBufferUsed = _snprintf(&buffer[bufferUsed],   
      bufferLeft, "   String: %s\n", s ); // C4996  
      // Note: _snprintf is deprecated; consider _snprintf_s instead  
      if (bSuccess = (perElementBufferUsed >= 0))  
      {  
         bufferUsed += perElementBufferUsed;  
         bufferLeft -= perElementBufferUsed;  
         if (bufferLeft > 0)  
         {  
            int perElementBufferUsed = _snprintf(&buffer[bufferUsed],   
            bufferLeft, "   Character: %c\n", c ); // C4996  
            if (bSuccess = (perElementBufferUsed >= 0))  
            {  
               bufferUsed += perElementBufferUsed;  
               bufferLeft -= perElementBufferUsed;  
               if (bufferLeft > 0)  
               {  
                  int perElementBufferUsed = _snprintf(&buffer  
                  [bufferUsed], bufferLeft, "   Integer: %d\n", i ); // C4996  
                  if (bSuccess = (perElementBufferUsed >= 0))  
                  {  
                     bufferUsed += perElementBufferUsed;  
                     bufferLeft -= perElementBufferUsed;  
                     if (bufferLeft > 0)  
                     {  
                        int perElementBufferUsed = _snprintf(&buffer  
                        [bufferUsed], bufferLeft, "   Real: %f\n", fp ); // C4996  
                        if (bSuccess = (perElementBufferUsed >= 0))  
                        {  
                           bufferUsed += perElementBufferUsed;  
                        }  
                     }  
                  }  
               }  
            }  
         }  
      }  
   }  
  
   if (!bSuccess)  
   {  
      printf("%s\n", "failure");  
   }  
   else  
   {  
      /* !store nul because _snprintf doesn't necessarily (if the string   
       * fits without the terminal nul, but not with it)!  
       * bufferUsed might be as large as bufferSize, which normally is   
       * like going one element beyond a buffer, but in this case   
       * subtracted one from bufferSize, so we're ok.  
       */  
      buffer[bufferUsed] = 0;  
      printf( "Output:\n%s\ncharacter count = %d\n", buffer, bufferUsed );  
   }  
   return EXIT_SUCCESS;  
}  
```  
  
```Output  
Output: String: computer Character: l Integer: 35 Real: 1.732053 character count = 69  
```  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [sprintf, \_sprintf\_l, swprintf, \_swprintf\_l, \_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [fprintf, \_fprintf\_l, fwprintf, \_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, \_printf\_l, wprintf, \_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf, \_scanf\_l, wscanf, \_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf, \_sscanf\_l, swscanf, \_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [vprintf \(Funciones\)](../../c-runtime-library/vprintf-functions.md)