---
title: "_vcprintf_s, _vcprintf_s_l, _vcwprintf_s, _vcwprintf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vcprintf_s"
  - "_vcprintf_s_l"
  - "_vcwprintf_s"
  - "_vcwprintf_s_l"
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
  - "vcprintf_s"
  - "vcwprintf_s_l"
  - "_vcwprintf_s"
  - "_vcwprintf_s_l"
  - "_vcprintf_s_l"
  - "_vtcprintf_s"
  - "vcwprintf_s"
  - "vcprintf_s_l"
  - "_vcprintf_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_vcprintf_s (función)"
  - "_vcprintf_s_l (función)"
  - "_vcwprintf_s (función)"
  - "_vcwprintf_s_l (función)"
  - "_vtcprintf_s (función)"
  - "_vtcprintf_s_l (función)"
  - "texto con formato [C++]"
  - "vcprintf_s (función)"
  - "vcprintf_s_l (función)"
  - "vcwprintf_s (función)"
  - "vcwprintf_s_l (función)"
  - "vtcprintf_s (función)"
  - "vtcprintf_s_l (función)"
ms.assetid: 5a46d45a-30db-45df-9850-455cbdac5636
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _vcprintf_s, _vcprintf_s_l, _vcwprintf_s, _vcwprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escribe salida con formato en la consola mediante un puntero a una lista de argumentos.  Estas versiones de [\_vcprintf, \_vcprintf\_l, \_vcwprintf, \_vcwprintf\_l](../../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _vcprintf(  
   const char* format,  
   va_list argptr  
);  
int _vcprintf(  
   const char* format,  
   locale_t locale,  
   va_list argptr  
);  
int _vcwprintf_s(  
   const wchar_t* format,  
   va_list argptr  
);  
int _vcwprintf_s_l(  
   const wchar_t* format,  
   locale_t locale,  
   va_list argptr  
);  
```  
  
#### Parámetros  
 `format`  
 Especificación de formato.  
  
 `argptr`  
 Puntero a la lista de argumentos.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
 Para obtener más información, vea [Sintaxis de especificación de formato: Funciones printf y wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## Valor devuelto  
 Número de caracteres escrito o un valor negativo si se produce un error en la salida.  
  
 Como las versiones menos seguras de estas funciones, si `format` es un puntero nulo, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Además, a diferencia de las versiones menos seguras de estas funciones, si `format` no especifica un formato válido, se genera una excepción de parámetro no válido.  Si la ejecución puede continuar, estas funciones devuelven un código de error y establecen `errno` en ese código de error.  El código de error predeterminado es `EINVAL` si no hay ningún valor más concreto.  
  
## Comentarios  
 Cada una de estas funciones toma un puntero a una lista de argumentos y, a continuación, aplica formato a los datos determinados y los escribe en la consola.  `_vcwprintf_s` es la versión con caracteres anchos de `_vcprintf_s`.  Toma una cadena de caracteres anchos como argumento.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro de configuración regional que se pasa en lugar de la configuración regional del subproceso actual.  
  
> [!IMPORTANT]
>  Asegúrese de que `format` no es una cadena definida por el usuario.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_vtcprintf_s`|`_vcprintf_s`|`_vcprintf_s`|`_vcwprintf_s`|  
|`_vtcprintf_s_l`|`_vcprintf_s_l`|`_vcprintf_s_l`|`_vcwprintf_s_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezados opcionales|  
|------------|--------------------------|----------------------------|  
|`_vcprintf_s`, `_vcprintf_s_l`|\<conio.h\> y \<stdarg.h\>|\<varargs.h\>\*|  
|`_vcwprintf_s`, `_vcwprintf_s_l`|\<conio.h\> o \<wchar.h\>, y \<stdarg.h\>|\<varargs.h\>\*|  
  
 \* Necesario para la compatibilidad con UNIX V.  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_vcprintf_s.cpp  
#include <conio.h>  
#include <stdarg.h>  
  
// An error formatting function used to print to the console.  
int eprintf_s(const char* format, ...)  
{  
  va_list args;  
  va_start(args, format);  
  return _vcprintf_s(format, args);  
}  
  
int main()  
{  
   eprintf_s("  (%d:%d): Error %s%d : %s\n", 10, 23, "C", 2111,  
           "<some error text>");  
   eprintf_s("  (Related to symbol '%s' defined on line %d).\n",  
           "<symbol>", 5 );  
}  
```  
  
  **\(10,23\): Error C2111: \<texto de error\>**  
 **\(Relacionado con el símbolo '\<símbolo\>' definido en la línea 5\).**   
## Equivalente en .NET Framework  
 [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [vprintf \(Funciones\)](../../c-runtime-library/vprintf-functions.md)   
 [\_cprintf, \_cprintf\_l, \_cwprintf, \_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [fprintf, \_fprintf\_l, fwprintf, \_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, \_printf\_l, wprintf, \_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, \_sprintf\_l, swprintf, \_swprintf\_l, \_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va\_arg, va\_copy, va\_end, va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)