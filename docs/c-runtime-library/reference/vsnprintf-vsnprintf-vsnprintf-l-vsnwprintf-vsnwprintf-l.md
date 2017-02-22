---
title: "vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vsnprintf"
  - "_vsnprintf_l"
  - "_vsnwprintf"
  - "_vsnwprintf_l"
  - "_vsnprintf"
  - "_vsnprintf;"
  - "vsnprintf; _vsnprintf"
  - "_vsnwprintf;"
  - "_vsnprintf_l;"
  - "_vsnwprintf_l;"
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
  - "ntoskrnl.exe"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_vsnprintf"
  - "_vsnwprintf"
  - "_vsntprintf"
  - "vsnprintf"
  - "stdio/vsnprintf"
  - "stdio/_vsnprintf"
  - "stdio/_vsnprintf_l"
  - "stdio/_vsnwprintf"
  - "stdio/_vsnwprintf_l"
  - "_vsnprintf_l"
  - "_vsnwprintf_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vsntprintf (función)"
  - "_vsnwprintf_l (función)"
  - "vsnwprintf_l (función)"
  - "vsntprintf_l (función)"
  - "_vsntprintf (función)"
  - "_vsnprintf_l (función)"
  - "vsnprintf (función)"
  - "_vsntprintf_l (función)"
  - "vsnprintf_l (función)"
  - "_vsnwprintf (función)"
  - "_vsnprintf (función)"
  - "texto con formato [C++]"
  - "vsnwprintf (función)"
ms.assetid: a97f92df-c2f8-4ea0-9269-76920d2d566a
caps.latest.revision: 35
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 35
---
# vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escribe un resultado con formato mediante un puntero a una lista de argumentos. Hay versiones más seguras de estas funciones disponibles; vea [vsnprintf\_s, \_vsnprintf\_s, \_vsnprintf\_s\_l, \_vsnwprintf\_s, \_vsnwprintf\_s\_l](../../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md).  
  
## Sintaxis  
  
```  
int vsnprintf(  
   char *buffer,  
   size_t count,  
   const char *format,  
   va_list argptr   
);  
int _vsnprintf(  
   char *buffer,  
   size_t count,  
   const char *format,  
   va_list argptr   
);  
int _vsnprintf_l(  
   char *buffer,  
   size_t count,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int _vsnwprintf(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vsnwprintf_l(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
template <size_t size>  
int vsnprintf(  
   char (&buffer)[size],  
   size_t count,  
   const char *format,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int _vsnprintf(  
   char (&buffer)[size],  
   size_t count,  
   const char *format,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int _vsnprintf_l(  
   char (&buffer)[size],  
   size_t count,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int _vsnwprintf(  
   wchar_t (&buffer)[size],  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int _vsnwprintf_l(  
   wchar_t (&buffer)[size],  
   size_t count,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
); // C++ only  
```  
  
#### Parámetros  
 `buffer`  
 Ubicación de almacenamiento del resultado.  
  
 `count`  
 Número máximo de caracteres que se van a escribir.  
  
 `format`  
 Especificación de formato.  
  
 `argptr`  
 Puntero a la lista de argumentos.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
 Para obtener más información, vea [Especificaciones de formato](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## Valor devuelto  
 El `vsnprintf` función devuelve el número de caracteres escritos, sin contar el carácter nulo de terminación. Si el tamaño de búfer especificado por `count` no es suficientemente grande para contener el resultado especificado por `format` y `argptr`, el valor devuelto de `vsnprintf` es el número de caracteres que se escribiría, sin contar el carácter null, si `count` fueron lo suficientemente grande. Si el valor devuelto es mayor que `count` \- 1, el resultado se ha truncado. Un valor devuelto de \-1 indica que se produjo un error de codificación.  
  
 Ambos `_vsnprintf` y `_vsnwprintf` funciones devuelven el número de caracteres escritos si el número de caracteres que se va a escribir es menor o igual que `count`; Si es mayor que el número de caracteres que se va a escribir `count`, estas funciones devuelven \-1 que indica que se ha truncado la salida.  
  
 El valor devuelto por todas estas funciones no incluye el carácter null final, si se escribe uno o no. Cuando `count` es cero, el valor devuelto es el número de caracteres que escriben las funciones, no incluir cualquier carácter null final. Puede usar este resultado para asignar suficiente espacio de búfer de la cadena y su carácter nulo y, a continuación, llame a la función para llenar el búfer.  
  
 Si `format` es `NULL`, o si `buffer` es NULL y `count` no es igual a cero, estas funciones invocan el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven \-1 y establecen `errno` en `EINVAL`.  
  
## Comentarios  
 Cada una de estas funciones toma un puntero a una lista de argumentos y, después, da formato a los datos y escribe hasta `count` caracteres en la memoria a la que apunta `buffer`. La función `vsnprintf` siempre escribe un terminador null, aunque trunque el resultado. Si se usan `_vsnprintf` y `_vsnwprintf`, el búfer terminará en null solo si hay espacio al final \(es decir, si el número de caracteres que se vayan a escribir es menor que `count`\).  
  
> [!IMPORTANT]
>  Para evitar ciertos tipos de riesgos de seguridad, asegúrese de que `format` no sea una cadena definida por el usuario. Para obtener más información, vea [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) \(Evitar saturaciones del búfer\).  
  
> [!NOTE]
>  Para garantizar que haya espacio para el valor null final al llamar a `_vsnprintf`, `_vsnprintf_l`, `_vsnwprintf` y `_vsnwprintf_l`, asegúrese de que `count` sea estrictamente inferior a la longitud del búfer e inicialice el búfer a un valor null antes de llamar a la función.  
>   
>  Dado que `vsnprintf` siempre escribe el carácter null final, el `count` parámetro puede ser igual que el tamaño del búfer.  
  
 A partir del UCRT de Visual Studio 2015 y Windows 10, la palabra clave `vsnprintf` ya no es idéntica a `_vsnprintf`. El `vsnprintf` función cumple con el estándar C99; `_vnsprintf` se conserva por compatibilidad con código antiguo de Visual Studio.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.  
  
 En C\+\+, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones. Para obtener más información, consulta [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_vsntprintf`|`_vsnprintf`|`_vsnprintf`|`_vsnwprintf`|  
|`_vsntprintf_l`|`_vsnprintf_l`|`_vsnprintf_l`|`_vsnwprintf_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario \(C\)|Encabezado necesario \(C\+\+\)|  
|------------|--------------------------------|------------------------------------|  
|`vsnprintf`, `_vsnprintf`, `_vsnprintf_l`|\<stdio.h\>|\<stdio.h\> o  \<cstdio\>|  
|`_vsnwprintf`, `_vsnwprintf_l`|\<stdio.h\> o \<wchar.h\>|\<stdio.h\>, \<wchar.h\>, \<cstdio\> o \<cwchar\>|  
  
 Las funciones `_vsnprintf`, `_vsnprintf_l`, `_vsnwprintf` y `_vsnwprintf_l` son específicas de Microsoft. Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```c  
// crt_vsnwprintf.c  
// compile by using: cl /W3 crt_vsnwprintf.c  
  
// To turn off error C4996, define this symbol:  
#define _CRT_SECURE_NO_WARNINGS  
  
#include <stdio.h>  
#include <wtypes.h>  
  
#define BUFFCOUNT (10)  
  
void FormatOutput(LPCWSTR formatstring, ...)  
{  
    int nSize = 0;  
    wchar_t buff[BUFFCOUNT];  
    memset(buff, 0, sizeof(buff));  
    va_list args;  
    va_start(args, formatstring);  
    // Note: _vsnwprintf is deprecated; consider vsnwprintf_s instead  
    nSize = _vsnwprintf(buff, BUFFCOUNT - 1, formatstring, args); // C4996  
    wprintf(L"nSize: %d, buff: %ls\n", nSize, buff);  
}  
  
int main() {  
    FormatOutput(L"%ls %ls", L"Hi", L"there");  
    FormatOutput(L"%ls %ls", L"Hi", L"there!");  
    FormatOutput(L"%ls %ls", L"Hi", L"there!!");  
}  
```  
  
```Output  
nSize: 8, aficionados: Hola allí nSize: 9, aficionados: Hola allí! nSize: -1, aficionados: Hola allí!  
```  
  
 Los cambios de comportamiento si usa vsnprintf en su lugar, junto con los parámetros de cadena de caracteres estrechos. El `count` parámetro puede ser todo el tamaño del búfer y el valor devuelto es el número de caracteres que se habrían escrito si `count` era lo suficientemente grande:  
  
## Ejemplo  
  
```c  
// crt_vsnprintf.c  
// compile by using: cl /W4 crt_vsnprintf.c  
#include <stdio.h>  
#include <stdarg.h> // for va_list, va_start  
#include <string.h> // for memset  
  
#define BUFFCOUNT (10)  
  
void FormatOutput(char* formatstring, ...)  
{  
    int nSize = 0;  
    char buff[BUFFCOUNT];  
    memset(buff, 0, sizeof(buff));  
    va_list args;  
    va_start(args, formatstring);  
    nSize = vsnprintf(buff, sizeof(buff), formatstring, args);  
    printf("nSize: %d, buff: %s\n", nSize, buff);  
}  
  
int main() {  
    FormatOutput("%s %s", "Hi", "there");   //  8 chars + null  
    FormatOutput("%s %s", "Hi", "there!");  //  9 chars + null  
    FormatOutput("%s %s", "Hi", "there!!"); // 10 chars + null  
}  
```  
  
```Output  
nSize: 8, aficionados: Hola allí nSize: 9, aficionados: Hola allí! nSize: 10, aficionados: Hola allí!  
```  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [vprintf \(Funciones\)](../../c-runtime-library/vprintf-functions.md)   
 [Sintaxis de especificación de formato: Funciones printf y wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [fprintf, \_fprintf\_l, fwprintf, \_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, \_printf\_l, wprintf, \_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, \_sprintf\_l, swprintf, \_swprintf\_l, \_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va\_arg, va\_copy, va\_end, va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)