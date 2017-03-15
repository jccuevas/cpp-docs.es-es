---
title: "_cprintf_s, _cprintf_s_l, _cwprintf_s, _cwprintf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_cwprintf_s_l"
  - "_cprintf_s_l"
  - "_cprintf_s"
  - "_cwprintf_s"
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
  - "_cwprintf_s_l"
  - "_cprintf_s"
  - "cwprintf_s"
  - "_cprintf_s_l"
  - "cwprintf_s_l"
  - "cprintf_s_l"
  - "_tcprintf_s"
  - "cprintf_s"
  - "_cwprintf_s"
  - "tcprintf_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_cprintf_s (función)"
  - "_cprintf_s_l (función)"
  - "_cwprintf_s (función)"
  - "_cwprintf_s_l (función)"
  - "_tcprintf_s (función)"
  - "_tcprintf_s_l (función)"
  - "cprintf_s (función)"
  - "cprintf_s_l (función)"
  - "cwprintf_s (función)"
  - "cwprintf_s_l (función)"
  - "tcprintf_s (función)"
  - "tcprintf_s_l (función)"
ms.assetid: c28504fe-0d20-4f06-8f97-ee33225922ad
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# _cprintf_s, _cprintf_s_l, _cwprintf_s, _cwprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Da formato e imprime en la consola.  Estas versiones de [\_cprintf, \_cprintf\_l, \_cwprintf, \_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _cprintf_s(   
   const char * format [,   
   argument] ...   
);  
int _cprintf_s_l(   
   const char * format,  
   locale_t locale [,   
   argument] ...   
);  
int _cwprintf_s(  
   const wchar * format [,   
   argument] ...  
);  
int _cwprintf_s_l(  
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
 Número de caracteres que se van a imprimir.  
  
## Comentarios  
 Estas funciones dan formato a una serie de caracteres y valores directamente en la consola, usando la función `_putch` \(`_putwch` en el caso de `_cwprintf_s`\) para generar los caracteres.  Cada `argument` \(si existe\) se convierte y sale según la especificación de formato correspondiente de `format`.  El formato tiene las mismas forma y función que el parámetro de `format` de la función [printf\_s](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  A diferencia de las funciones `fprintf_s`, `printf_s` y `sprintf_s`, ni `_cprintf_s` ni `_cwprintf_s` convierten los caracteres de salto de línea en combinaciones retorno de carro\-salto de línea \(CR\-LF\) en sus resultados.  
  
 Una diferencia importante es que `_cwprintf_s` muestra caracteres Unicode cuando se usa en Windows NT.  A diferencia de `_cprintf_s`, `_cwprintf_s` usa la configuración regional actual de la consola.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional actual.  
  
> [!IMPORTANT]
>  Asegúrese de que `format` no es una cadena definida por el usuario.  
  
 Al igual que las versiones no seguras \(vea [\_cprintf, \_cprintf\_l, \_cwprintf, \_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)\), estas funciones validan sus parámetros e invocan el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md), si `format` es un puntero nulo.  Estas funciones se diferencian de las versiones no seguras en que también se valida la propia cadena de formato.  Si hay algún especificador de formato desconocido o con formato incorrecto, estas funciones invocan el controlador de parámetros no válidos.  En todos los casos, si la ejecución puede continuar, las funciones devuelven \-1 y establecen `errno` en `EINVAL`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcprintf_s`|`_cprintf_s`|`_cprintf_s`|`_cwprintf_s`|  
|`_tcprintf_s_l`|`_cprintf_s_l`|`_cprintf_s_l`|`_cwprintf_s_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_cprintf_s`,`_cprintf_s_l`|\<conio.h\>|  
|`_cwprintf_s`, `_cwprintf_s_l`|\<conio.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_cprintf_s.c  
// compile with: /c  
// This program displays some variables to the console.  
  
#include <conio.h>  
  
int main( void )  
{  
   int      i = -16, h = 29;  
   unsigned u = 62511;  
   char     c = 'A';  
   char     s[] = "Test";  
  
   /* Note that console output does not translate \n as  
    * standard output does. Use \r\n instead.  
    */  
   _cprintf_s( "%d  %.4x  %u  %c %s\r\n", i, h, u, c, s );  
}  
```  
  
## Resultados  
  
```  
-16  001d  62511  A Test  
```  
  
## Vea también  
 [E\/S de consola y de puerto](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cscanf, \_cscanf\_l, \_cwscanf, \_cwscanf\_l](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)   
 [fprintf\_s, \_fprintf\_s\_l, fwprintf\_s, \_fwprintf\_s\_l](../../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)   
 [printf\_s, \_printf\_s\_l, wprintf\_s, \_wprintf\_s\_l](../../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [sprintf\_s, \_sprintf\_s\_l, swprintf\_s, \_swprintf\_s\_l](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)   
 [vfprintf\_s, \_vfprintf\_s\_l, vfwprintf\_s, \_vfwprintf\_s\_l](../../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)   
 [Sintaxis de especificación de formato: Funciones printf y wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)