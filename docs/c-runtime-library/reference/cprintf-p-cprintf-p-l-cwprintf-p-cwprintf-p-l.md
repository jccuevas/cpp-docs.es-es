---
title: "_cprintf_p, _cprintf_p_l, _cwprintf_p, _cwprintf_p_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_cprintf_p_l"
  - "_cwprintf_p_l"
  - "_cwprintf_p"
  - "_cprintf_p"
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
  - "cprintf_p"
  - "cwprintf_p"
  - "tcprintf_p"
  - "_cwprintf_p_l"
  - "_cprintf_p"
  - "csprintf_p_l"
  - "_cprintf_p_l"
  - "_cwprintf_p"
  - "_tcprintf_p"
  - "cprintf_p_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_cprintf_p (función)"
  - "_cprintf_p_l (función)"
  - "_cwprintf_p (función)"
  - "_cwprintf_p_l (función)"
  - "_tcprintf_p (función)"
  - "_tcprintf_p_l (función)"
  - "cprintf_p (función)"
  - "cprintf_p_l (función)"
  - "cwprintf_p (función)"
  - "cwprintf_p_l (función)"
  - "tcprintf_p (función)"
  - "tcprintf_p_l (función)"
ms.assetid: 1f82fd7d-13c8-4c4a-a3e4-db0df3873564
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# _cprintf_p, _cprintf_p_l, _cwprintf_p, _cwprintf_p_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Da formato e imprime en la consola, y admite parámetros posicionales en la cadena de formato.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _cprintf_p(   
   const char * format [,   
   argument] ...   
);  
int _cprintf_p_l(   
   const char * format,  
   locale_t locale [,   
   argument] ...   
);  
int _cwprintf_p(  
   const wchar * format [,   
   argument] ...  
);  
int _cwprintf_p_l(  
   const wchar * format,  
   locale_t locale [,  
   argument] ...  
);  
```  
  
#### Parámetros  
 `format`  
 Cadena de control de formato.  
  
 `argument`  
 Parámetros opcionales.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Número de caracteres impreso o un valor negativo si se produce un error.  
  
## Comentarios  
 Estas funciones dan formato a una serie de caracteres y valores directamente en la consola, y la imprimen, mediante las funciones `_putch` y `_putwch` para producir caracteres.  Cada `argument` \(si existe\) se convierte y sale según la especificación de formato correspondiente de `format`.  El formato tiene las mismas forma y función que el parámetro de `format` de la función [printf\_p](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  La diferencia entre `_cprintf_p` y `cprintf_s` es que `_cprintf_p` admite parámetros posicionales, lo que permite especificar el orden en el que se usan los argumentos en la cadena de formato.  Para obtener más información, vea el tema sobre [printf\_p \(Parámetros de posición\)](../../c-runtime-library/printf-p-positional-parameters.md).  
  
 A diferencia de las funciones `fprintf_p`, `printf_p` y `sprintf_p`, ni `_cprintf_p` ni `_cwprintf_p` convierten los caracteres de salto de línea en combinaciones retorno de carro\-salto de línea \(CR\-LF\) en sus resultados.  Una diferencia importante es que `_cwprintf_p` muestra caracteres Unicode cuando se usa en Windows NT.  A diferencia de `_cprintf_p`, `_cwprintf_p` usa la configuración regional actual de la consola.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional actual.  
  
> [!IMPORTANT]
>  Asegúrese de que `format` no es una cadena definida por el usuario.  
  
 Además, al igual que `_cprintf_s` y `_cwprintf_s`, validan el puntero de entrada y la cadena de formato.  Si `format` o `argument` es `NULL`, o si la cadena de formato contiene caracteres de formato no válidos, estas funciones invocan el controlador de parámetros no válidos, tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven \-1 y establecen `errno` en `EINVAL`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcprintf_p`|`_cprintf_p`|`_cprintf_p`|`_cwprintf_p`|  
|`_tcprintf_p_l`|`_cprintf_p_l`|`_cprintf_p_l`|`_cwprintf_p_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_cprintf_p`,`_cprintf_p_l`|\<conio.h\>|  
|`_cwprintf_p`,`_cwprintf_p_l`|\<conio.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_cprintf_p.c  
// This program displays some variables to the console  
// using the _cprintf_p function.  
  
#include <conio.h>  
  
int main( void )  
{  
    int         i = -16,  
                h = 29;  
    unsigned    u = 62511;  
    char        c = 'A';  
    char        s[] = "Test";  
  
    // Note that console output does not translate  
    // \n as standard output does. Use \r\n instead.  
    _cprintf_p( "%2$d  %1$.4x  %3$u  %4$c %5$s\r\n",   
                h, i, u, c, s );  
}  
```  
  
  **\-16  001d  62511  A Test**   
## Vea también  
 [E\/S de consola y de puerto](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cscanf, \_cscanf\_l, \_cwscanf, \_cwscanf\_l](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)   
 [\_cscanf\_s, \_cscanf\_s\_l, \_cwscanf\_s, \_cwscanf\_s\_l](../../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)   
 [\_fprintf\_p, \_fprintf\_p\_l, \_fwprintf\_p, \_fwprintf\_p\_l](../../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)   
 [fprintf\_s, \_fprintf\_s\_l, fwprintf\_s, \_fwprintf\_s\_l](../../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)   
 [\_printf\_p, \_printf\_p\_l, \_wprintf\_p, \_wprintf\_p\_l](../../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)   
 [printf\_s, \_printf\_s\_l, wprintf\_s, \_wprintf\_s\_l](../../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [\_sprintf\_p, \_sprintf\_p\_l, \_swprintf\_p, \_swprintf\_p\_l](../../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)   
 [\_vfprintf\_p, \_vfprintf\_p\_l, \_vfwprintf\_p, \_vfwprintf\_p\_l](../../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)   
 [\_cprintf\_s, \_cprintf\_s\_l, \_cwprintf\_s, \_cwprintf\_s\_l](../../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)   
 [printf\_p \(Parámetros de posición\)](../../c-runtime-library/printf-p-positional-parameters.md)   
 [Sintaxis de especificación de formato: Funciones printf y wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)