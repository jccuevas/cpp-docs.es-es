---
title: "_vcprintf_p, _vcprintf_p_l, _vcwprintf_p, _vcwprintf_p_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vcprintf_p"
  - "_vcwprintf_p_l"
  - "_vcprintf_p_l"
  - "_vcwprintf_p"
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
  - "vcwprintf_p"
  - "vcprintf_p_l"
  - "_vcprintf_p"
  - "_vcprintf_p_l"
  - "vcwprintf_p_l"
  - "vcprintf_p"
  - "_vcwprintf_p"
  - "_vcwprintf_p_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_vcprintf_p (función)"
  - "_vcprintf_p_l (función)"
  - "_vcwprintf_p (función)"
  - "_vcwprintf_p_l (función)"
  - "_vtcprintf_p (función)"
  - "_vtcprintf_p_l (función)"
  - "vcprintf_p (función)"
  - "vcprintf_p_l (función)"
  - "vcwprintf_p (función)"
  - "vcwprintf_p_l (función)"
  - "vtcprintf_p (función)"
  - "vtcprintf_p_l (función)"
ms.assetid: 611024cc-90e7-41db-8e85-145ca95012b1
caps.latest.revision: 20
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _vcprintf_p, _vcprintf_p_l, _vcwprintf_p, _vcwprintf_p_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escribe la salida con formato en la consola mediante un puntero a una lista de argumentos y admite parámetros posicionales en la cadena de formato.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _vcprintf_p(  
   const char* format,  
   va_list argptr  
);  
int _vcprintf_p_l(  
   const char* format,  
   locale_t locale,  
   va_list argptr  
);  
int _vcwprintf_p(  
   const wchar_t* format,  
   va_list argptr  
);  
int _vcwprintf_p_l(  
   const wchar_t* format,  
   locale_t locale,  
   va_list argptr  
);  
```  
  
#### Parámetros  
 `format`  
 Especificación de formato.  
  
 `argptr`  
 Puntero a una lista de argumentos.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
 Para obtener más información, vea [Sintaxis de especificación de formato: Funciones printf y wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## Valor devuelto  
 Número de caracteres escritos o un valor negativo si se produce un error en la salida.  Si `format` es un puntero nulo, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y se devuelve \-1.  
  
## Comentarios  
 Cada una de estas funciones toma un puntero a una lista de argumentos y luego usa la función `_putch` para aplicar formato a los datos y escribirlos en la consola.  \(`_vcwprintf_p` usa `_putwch` en lugar de `_putch`.  `_vcwprintf_p` es la versión con caracteres anchos de `_vcprintf_p`.  Toma una cadena de caracteres anchos como argumento\).  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro de configuración regional que se pasa en lugar de la configuración regional del subproceso actual.  
  
 Cada `argument` \(si existe\) se convierte y se muestra según la especificación de formato correspondiente de `format`.  La especificación de formato admite parámetros posicionales, lo que permite especificar el orden en el que se usan los argumentos en la cadena de formato.  Para obtener más información, vea el tema sobre [printf\_p \(Parámetros de posición\)](../../c-runtime-library/printf-p-positional-parameters.md).  
  
 Estas funciones no convierten los caracteres de avance de línea en combinaciones retorno de carro\-avance de línea \(CR\-LF\) cuando producen valores de salida.  
  
> [!IMPORTANT]
>  Asegúrese de que `format` no es una cadena definida por el usuario.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
 Estas funciones validan el puntero de entrada y la cadena de formato.  Si `format` o `argument` es `NULL`, o la cadena de formato contiene caracteres de formato no válidos, estas funciones invocan el controlador de parámetros no válidos, tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven \-1 y establecen `errno` en `EINVAL`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_vtcprintf_p`|`_vcprintf_p`|`_vcprintf_p`|`_vcwprintf_p`|  
|`_vtcprintf_p_l`|`_vcprintf_p_l`|`_vcprintf_p_l`|`_vcwprintf_p_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_vcprintf_p`, `_vcprintf_p_l`|\<conio.h\> y \<stdarg.h\>|  
|`_vcwprintf_p`, `_vcwprintf_p_l`|\<conio.h\> y \<stdarg.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_vcprintf_p.c  
// compile with: /c  
#include <conio.h>  
#include <stdarg.h>  
  
// An error formatting function that's used to print to the console.  
int eprintf(const char* format, ...)  
{  
  va_list args;  
  va_start(args, format);  
  return _vcprintf_p(format, args);  
}  
  
int main()  
{  
   int n = eprintf("parameter 2 = %2$d; parameter 1 = %1$s\r\n",  
      "one", 222);  
   _cprintf_s("%d characters printed\r\n");  
}  
```  
  
  **parámetro 2 \= 222; parámetro 1 \= one**  
**38 caracteres impresos**   
## Vea también  
 [E\/S de consola y de puerto](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cprintf, \_cprintf\_l, \_cwprintf, \_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [va\_arg, va\_copy, va\_end, va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)   
 [printf\_p \(Parámetros de posición\)](../../c-runtime-library/printf-p-positional-parameters.md)