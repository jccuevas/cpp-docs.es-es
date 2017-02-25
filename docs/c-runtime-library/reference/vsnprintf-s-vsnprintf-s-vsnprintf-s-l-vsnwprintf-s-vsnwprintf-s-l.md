---
title: "vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vsnwprintf_s"
  - "_vsnwprintf_s_l"
  - "_vsnprintf_s"
  - "vsnprintf_s"
  - "_vsnprintf_s_l"
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
  - "_vsnprintf_s"
  - "_vsntprintf_s"
  - "_vsnwprintf_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_vsnprintf_s (función)"
  - "_vsnprintf_s_l (función)"
  - "_vsntprintf_s (función)"
  - "_vsntprintf_s_l (función)"
  - "_vsnwprintf_s (función)"
  - "_vsnwprintf_s_l (función)"
  - "texto con formato [C++]"
  - "vsnprintf_s (función)"
  - "vsnprintf_s_l (función)"
  - "vsntprintf_s (función)"
  - "vsntprintf_s_l (función)"
  - "vsnwprintf_s (función)"
  - "vsnwprintf_s_l (función)"
ms.assetid: 147ccfce-58c7-4681-a726-ef54ac1c604e
caps.latest.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 32
---
# vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escribe un resultado con formato mediante un puntero a una lista de argumentos.  Estas versiones de [vsnprintf, \_vsnprintf, \_vsnprintf\_l, \_vsnwprintf, \_vsnwprintf\_l](../../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
int vsnprintf_s(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format,  
   va_list argptr   
);  
int _vsnprintf_s(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format,  
   va_list argptr   
);  
int _vsnprintf_s_l(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int _vsnwprintf_s(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vsnwprintf_s_l(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
template <size_t size>  
int _vsnprintf_s(  
   char (&buffer)[size],  
   size_t count,  
   const char *format,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int _vsnwprintf_s(  
   wchar_t (&buffer)[size],  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
); // C++ only  
```  
  
#### Parámetros  
 `buffer`  
 Ubicación de almacenamiento del resultado.  
  
 `sizeOfBuffer`  
 Tamaño de `buffer` para el resultado, en número de caracteres.  
  
 `count`  
 Número máximo de caracteres que se van a escribir \(sin incluir el valor final nulo\), o [\_TRUNCATE](../../c-runtime-library/truncate.md).  
  
 `format`  
 Especificación de formato.  
  
 `argptr`  
 Puntero a la lista de argumentos.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
 Para obtener más información, vea [Especificaciones de formato](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## Valor devuelto  
 `vsnprintf_s`,`_vsnprintf_s` y `_vsnwprintf_s` devuelven el número de caracteres escritos, sin incluir el carácter de terminación nulo, o un valor negativo si se produce un error de salida.  `vsnprintf_s` es idéntica a `_vsnprintf_s`.  `vsnprintf_s` se incluye por razones de compatibilidad con el estándar ANSI.  La clase `_vnsprintf` se conserva por razones de compatibilidad con versiones anteriores.  
  
 Si el almacenamiento necesario para almacenar los datos y un carácter final nulo es mayor que `sizeOfBuffer`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md), a menos que `count` sea [\_TRUNCATE](../../c-runtime-library/truncate.md), en cuyo caso se escribe la parte de la cadena que quepa en `buffer` y se devuelve \-1.  Si la ejecución continúa después del controlador de parámetros no válidos, estas funciones establecen `buffer` en una cadena vacía, establecen `errno` en `ERANGE` y devuelven \-1.  
  
 Si `buffer` o `format` es un puntero `NULL`, o si `count` es menor o igual que cero, se invoca el controlador de parámetros no válidos.  Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven \-1.  
  
### Condiciones de error  
  
|`Condition`|Devolución|`errno`|  
|-----------------|----------------|-------------|  
|`buffer` es `NULL`.|\-1|`EINVAL`|  
|`format` es `NULL`.|\-1|`EINVAL`|  
|`count` \<\= 0|\-1|`EINVAL`|  
|`sizeOfBuffer` es demasiado pequeño \(y `count` \!\= `_TRUNCATE`\)|\-1 \(y `buffer` se establece en una cadena vacía\)|`ERANGE`|  
  
## Comentarios  
 Cada una de estas funciones toma un puntero a una lista de argumentos, después da formato a un máximo de `count` caracteres, y los escribe, de los datos especificados en la memoria a la que señala `buffer` y anexa un carácter nulo final.  
  
 Si `count` es [\_TRUNCATE](../../c-runtime-library/truncate.md), estas funciones escriben la parte de la cadena que quepa en `buffer` y dejan espacio para un carácter nulo final.  Si toda la cadena \(con el valor nulo final\) cabe en `buffer`, estas funciones devuelven el número de caracteres escrito \(sin incluir el valor nulo final\); de lo contrario, devuelven \-1 para indicar que se ha producido truncamiento.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.  
  
> [!IMPORTANT]
>  Asegúrese de que `format` no es una cadena definida por el usuario.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
> [!NOTE]
>  Para asegurarse de que hay espacio para el valor nulo final, asegúrese de que `count` es claramente menor que la longitud del búfer, o use `_TRUNCATE`.  
  
 En C\+\+, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer \(lo que elimina la necesidad de especificar un argumento de tamaño\) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_vsntprintf_s`|`_vsnprintf_s`|`_vsnprintf_s`|`_vsnwprintf_s`|  
|`_vsntprintf_s_l`|`_vsnprintf_s_l`|`_vsnprintf_s_l`|`_vsnwprintf_s_l`|  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezados opcionales|  
|------------|--------------------------|----------------------------|  
|`vsnprintf_s`|\<stdio.h\> y \<stdarg.h\>|\<varargs.h\>\*|  
|`_vsnprintf_s`, `_vsnprintf_s_l`|\<stdio.h\> y \<stdarg.h\>|\<varargs.h\>\*|  
|`_vsnwprintf_s`, `_vsnwprintf_s_l`|\<stdio.h\> o \<wchar.h\>, y \<stdarg.h\>|\<varargs.h\>\*|  
  
 \* Necesario para la compatibilidad con UNIX V.  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_vsnprintf_s.cpp  
#include <stdio.h>  
#include <wtypes.h>  
  
void FormatOutput(LPCSTR formatstring, ...)   
{  
   int nSize = 0;  
   char buff[10];  
   memset(buff, 0, sizeof(buff));  
   va_list args;  
   va_start(args, formatstring);  
   nSize = vsnprintf_s( buff, _countof(buff), _TRUNCATE, formatstring, args);  
   printf("nSize: %d, buff: %s\n", nSize, buff);  
}  
  
int main() {  
   FormatOutput("%s %s", "Hi", "there");  
   FormatOutput("%s %s", "Hi", "there!");  
   FormatOutput("%s %s", "Hi", "there!!");  
}  
```  
  
  **nSize: 8, buff: Hi there**  
**nSize: 9, buff: Hi there\!**  
**nSize: \-1, buff: Hi there\!**   
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [vprintf \(Funciones\)](../../c-runtime-library/vprintf-functions.md)   
 [fprintf, \_fprintf\_l, fwprintf, \_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, \_printf\_l, wprintf, \_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, \_sprintf\_l, swprintf, \_swprintf\_l, \_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va\_arg, va\_copy, va\_end, va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)