---
title: "_cscanf, _cscanf_l, _cwscanf, _cwscanf_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_cscanf_l"
  - "_cscanf"
  - "_cwscanf"
  - "_cwscanf_l"
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
  - "_cwscanf"
  - "cwscanf_l"
  - "tcscanf_l"
  - "_tcscanf_l"
  - "_cscanf"
  - "_cscanf_l"
  - "tcscanf"
  - "cwscanf"
  - "_cwscanf_l"
  - "cscanf_l"
  - "_tcscanf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_cscanf (función)"
  - "_cscanf_l (función)"
  - "_cwscanf (función)"
  - "_cwscanf_l (función)"
  - "_tcscanf (función)"
  - "_tcscanf_l (función)"
  - "cscanf_l (función)"
  - "cwscanf (función)"
  - "cwscanf_l (función)"
  - "datos [C++], leer en la consola"
  - "leer datos [C++], en la consola"
  - "tcscanf (función)"
  - "tcscanf_l (función)"
ms.assetid: dbfe7547-b577-4567-a1cb-893fa640e669
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# _cscanf, _cscanf_l, _cwscanf, _cwscanf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Lee datos con formato de la consola.  Hay disponibles versiones más seguras de estas funciones; vea [\_cscanf\_s, \_cscanf\_s\_l, \_cwscanf\_s, \_cwscanf\_s\_l](../../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md).  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _cscanf(   
   const char *format [,  
   argument] ...   
);  
int _cscanf_l(   
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int _cwscanf(   
   const wchar_t *format [,  
   argument] ...   
);  
int _cwscanf_l(   
   const wchar_t *format,  
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
 Número de campos que se convirtieron y asignaron correctamente.  El valor devuelto no incluye los campos que se leyeron pero no se asignaron.  El valor devuelto es `EOF` para un intento de lectura al final del archivo.  Esto puede tener lugar cuando la entrada de teclado se redirige en el nivel de la línea de comandos del sistema operativo.  Un valor devuelto de 0 indica que no se ha asignado ningún campo.  
  
## Comentarios  
 La función `_cscanf` lee datos directamente de la consola en las ubicaciones especificadas por `argument`.  La función [\_getche](../../c-runtime-library/reference/getch-getwch.md) se utiliza para leer caracteres.  Cada parámetro opcional debe ser un puntero a una variable con un tipo que se corresponda con un especificador de tipo en `format`.  El formato controla la interpretación de los campos de entrada, y tiene la misma forma y función que el parámetro `format` de la función [scanf](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md).  Si bien `_cscanf` suele repetir el carácter de entrada, no lo hace si la última llamada se hizo a `_ungetch`.  
  
 Esta función valida sus parámetros.  Si format es NULL, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `EOF`.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcscanf`|`_cscanf`|`_cscanf`|`_cwscanf`|  
|`_tcscanf_l`|`_cscanf_l`|`_cscanf_l`|`_cwscanf_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_cscanf`,`_cscanf_l`|\<conio.h\>|  
|`_cwscanf`, `_cwscanf_l`|\<conio.h\> o \<wchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_cscanf.c  
// compile with: /c /W3  
/* This program prompts for a string  
 * and uses _cscanf to read in the response.  
 * Then _cscanf returns the number of items  
 * matched, and the program displays that number.  
 */  
  
#include <stdio.h>  
#include <conio.h>  
  
int main( void )  
{  
   int   result, i[3];  
  
   _cprintf_s( "Enter three integers: ");  
   result = _cscanf( "%i %i %i", &i[0], &i[1], &i[2] ); // C4996  
   // Note: _cscanf is deprecated; consider using _cscanf_s instead  
   _cprintf_s( "\r\nYou entered " );  
   while( result-- )  
      _cprintf_s( "%i ", i[result] );  
   _cprintf_s( "\r\n" );  
}  
```  
  
## Entrada  
  
```  
1 2 3  
```  
  
## Resultados  
  
```  
Enter three integers: 1 2 3  
You entered 3 2 1  
```  
  
## Vea también  
 [E\/S de consola y de puerto](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cprintf, \_cprintf\_l, \_cwprintf, \_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [fscanf, \_fscanf\_l, fwscanf, \_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [scanf\_s, \_scanf\_s\_l, wscanf\_s, \_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [sscanf, \_sscanf\_l, swscanf, \_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)