---
title: "_cputs, _cputws | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_cputws"
  - "_cputs"
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
  - "api-ms-win-crt-conio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "cputws"
  - "_cputs"
  - "_cputws"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_cputs (función)"
  - "_cputws (función)"
  - "consola, enviar cadenas"
  - "cputs (función)"
  - "cputws (función)"
  - "colocar cadenas en la consola"
  - "cadenas [C++], escribir"
ms.assetid: ec418484-0f8d-43ec-8d8b-198a556c659e
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# _cputs, _cputws
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Coloca una cadena en la consola.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
  
        int _cputs(   
const char *str   
);  
int _cputws(  
const wchar_t *str   
);  
```  
  
#### Parámetros  
 `str`  
 Cadena de salida  
  
## Valor devuelto  
 Si la operación se realiza correctamente, `_cputs` devuelve 0.  Si se produce un error en la función, devuelve un valor distinto de cero.  
  
## Comentarios  
 La `_cputs` función escribe la cadena terminada en null a la que `str` apunta directamente en la consola.  No se anexa ninguna combinación de retorno de carro y salto de línea \(CR\-LF\) automáticamente a la cadena.  
  
 Esta función valida su parámetro.  Si `str` es **NULL**, se invoca el controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y se devuelve \-1.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|**\_cputts**|`_cputs`|`_cputs`|`_cputws`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_cputs`|\<conio.h\>|\<errno.h\>|  
|`_cputws`|\<conio.h\>|\<errno.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_cputs.c  
// compile with: /c  
// This program first displays a string to the console.  
  
#include <conio.h>  
#include <errno.h>  
  
void print_to_console(char* buffer)  
{  
   int retval;  
   retval = _cputs( buffer );  
   if (retval)  
   {  
       if (errno == EINVAL)  
       {  
         _cputs( "Invalid buffer in print_to_console.\r\n");  
       }  
       else  
         _cputs( "Unexpected error in print_to_console.\r\n");  
   }  
}  
  
void wprint_to_console(wchar_t* wbuffer)  
{  
   int retval;  
   retval = _cputws( wbuffer );  
   if (retval)  
   {  
       if (errno == EINVAL)  
       {  
         _cputws( L"Invalid buffer in wprint_to_console.\r\n");  
       }  
       else  
         _cputws( L"Unexpected error in wprint_to_console.\r\n");  
   }  
}  
  
int main()  
{  
  
   // String to print at console.   
   // Notice the \r (return) character.   
   char* buffer = "Hello world (courtesy of _cputs)!\r\n";  
   wchar_t *wbuffer = L"Hello world (courtesy of _cputws)!\r\n";  
   print_to_console(buffer);  
   wprint_to_console( wbuffer );  
}  
```  
  
## Salida  
  
```  
Hello world (courtesy of _cputs)!  
Hello world (courtesy of _cputws)!  
```  
  
## Vea también  
 [E\/S de consola y de puerto](../../c-runtime-library/console-and-port-i-o.md)   
 [\_putch, \_putwch](../../c-runtime-library/reference/putch-putwch.md)