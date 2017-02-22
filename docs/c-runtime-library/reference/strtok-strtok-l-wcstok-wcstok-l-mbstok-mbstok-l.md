---
title: "strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbstok_l"
  - "_mbstok"
  - "wcstok"
  - "_mbstok"
  - "strtok"
  - "_wcstok_l"
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
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_mbstok"
  - "strtok"
  - "_tcstok"
  - "wcstok"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbstok (función)"
  - "_mbstok_l (función)"
  - "_strtok_l (función)"
  - "_tcstok (función)"
  - "_tcstok_l (función)"
  - "_wcstok_l (función)"
  - "mbstok (función)"
  - "mbstok_l (función)"
  - "cadenas [C++], buscar"
  - "strtok (función)"
  - "strtok_l (función)"
  - "tcstok (función)"
  - "tcstok_l (función)"
  - "tokens, buscar en cadenas"
  - "wcstok (función)"
  - "wcstok_l (función)"
ms.assetid: 904cb734-f0d7-4d77-ba81-4791ddf461ae
caps.latest.revision: 34
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 34
---
# strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Busca el siguiente token en una cadena, con la configuración regional actual o con la configuración regional especificada que se pase.  Hay disponibles versiones más seguras de estas funciones; vea [strtok\_s, \_strtok\_s\_l, wcstok\_s, \_wcstok\_s\_l, \_mbstok\_s, \_mbstok\_s\_l](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md).  
  
> [!IMPORTANT]
>  `_mbstok` y `_mbstok_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
char *strtok(  
   char *strToken,  
   const char *strDelimit   
);  
wchar_t *wcstok(  
   wchar_t *strToken,  
   const wchar_t *strDelimit   
);  
unsigned char *_mbstok(  
   unsigned char*strToken,  
   const unsigned char *strDelimit   
);  
unsigned char *_mbstok(  
   unsigned char*strToken,  
   const unsigned char *strDelimit,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `strToken`  
 Cadena que contiene tokens.  
  
 `strDelimit`  
 Juego de caracteres delimitadores.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Devuelve un puntero al siguiente token que se encuentra en `strToken`.  Devuelven `NULL` cuando no se encuentran más tokens.  Cada llamada modifica `strToken` sustituyendo un carácter `NULL` por el primer delimitador que aparece después del token devuelto.  
  
## Comentarios  
 La función `strtok` busca el siguiente token en `strToken`.  El juego de caracteres de `strDelimit` especifica los delimitadores posibles del token que se van a buscar en `strToken` en la llamada actual.  `wcstok` y `_mbstok` son versiones de caracteres anchos y multibyte de `strtok`.  Los argumentos y el valor devuelto de `wcstok` son cadenas de caracteres anchos; los de `_mbstok` son cadenas de caracteres multibyte.  Estas tres funciones se comportan exactamente igual.  
  
> [!IMPORTANT]
>  Estas funciones representan una posible amenaza por un problema de saturación del búfer.  Los problemas de saturación del búfer son un método frecuente de ataque del sistema, que produce una elevación de privilegios no justificada.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
 En la primera llamada a `strtok`, la función omite los delimitadores iniciales y devuelve un puntero al primer token de `strToken`, y finaliza el token con un carácter nulo.  Del resto de `strToken` se pueden extraer más tokens mediante una serie de llamadas a `strtok`.  Cada llamada a `strtok`modifica `strToken` insertando un carácter nulo después del `token` devuelto por la llamada.  Para leer el token siguiente de `strToken`, llame a `strtok` con un valor `NULL` para el argumento de `strToken`.  El argumento `NULL` de `strToken` hace que `strtok` busque el token siguiente en el parámetro `strToken` modificado.  El argumento `strDelimit` acepta cualquier valor de una llamada a la siguiente, por lo que el juego de delimitadores puede variar.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en su lugar.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
> [!NOTE]
>  Cada función usa una variable estática local de subproceso para dividir la cadena en tokens.  Por consiguiente, varios subprocesos pueden llamar simultáneamente a estas funciones sin que se produzcan efectos no deseados.  Sin embargo, dentro de un único subproceso, la intercalación de llamadas a una de estas funciones generará probablemente daños en los datos y resultados poco precisos.  Al analizar diferentes cadenas, termine de analizar una cadena antes de empezar a analizar la siguiente.  Además, tenga en cuenta el riesgo que puede existir al llamar a una de estas funciones dentro de un bucle donde se llama a otra función.  Si la otra función usa una de estas funciones, se producirá una secuencia intercalada de llamadas y se generarán daños en los datos.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcstok`|`strtok`|`_mbstok`|`wcstok`|  
|`_tcstok`|`_strtok_l`|`_mbstok_l`|`_wcstok_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strtok`|\<string.h\>|  
|`wcstok`|\<string.h\> o \<wchar.h\>|  
|`_mbstok`, `_mbstok_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_strtok.c  
// compile with: /W3  
// In this program, a loop uses strtok  
// to print all the tokens (separated by commas  
// or blanks) in the string named "string".  
//  
#include <string.h>  
#include <stdio.h>  
  
char string[] = "A string\tof ,,tokens\nand some  more tokens";  
char seps[]   = " ,\t\n";  
char *token;  
  
int main( void )  
{  
   printf( "Tokens:\n" );  
  
   // Establish string and get the first token:  
   token = strtok( string, seps ); // C4996  
   // Note: strtok is deprecated; consider using strtok_s instead  
   while( token != NULL )  
   {  
      // While there are tokens in "string"  
      printf( " %s\n", token );  
  
      // Get next token:   
      token = strtok( NULL, seps ); // C4996  
   }  
}  
```  
  
  **Tokens:**  
 **A**  
 **string**  
 **de**  
 **tokens**  
 **y**  
 **some**  
 **more**  
 **tokens**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcspn, wcscspn, \_mbscspn, \_mbscspn\_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [strspn, wcsspn, \_mbsspn, \_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)