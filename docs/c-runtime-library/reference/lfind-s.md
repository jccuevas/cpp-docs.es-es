---
title: "_lfind_s | Microsoft Docs"
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
  - "_lfind_s"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "lfind_s"
  - "_lfind_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_lfind_s (función)"
  - "matrices [CRT], buscar"
  - "claves, buscar en matrices"
  - "lfind_s (función)"
  - "búsqueda lineal"
  - "buscar, lineales"
ms.assetid: f1d9581d-5c9d-4222-a31c-a6dfafefa40d
caps.latest.revision: 26
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _lfind_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Realiza una búsqueda lineal para la clave especificada.  Una versión de [\_lfind](../../c-runtime-library/reference/lfind.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
void *_lfind_s(  
   const void *key,  
   const void *base,  
   unsigned int *num,  
   size_t size,  
   int (__cdecl *compare)(void *, const void *, const void *),  
   void * context  
);  
```  
  
#### Parámetros  
 `key`  
 Objeto para buscar.  
  
 `base`  
 Puntero a la base de datos de búsqueda.  
  
 `num`  
 Número de elementos de la matriz.  
  
 `size`  
 Tamaño de los elementos de matriz de bytes.  
  
 `compare`  
 Puntero a la rutina de comparación.  El primer parámetro es el puntero de `context` .  El segundo parámetro es un puntero a cerrar para la búsqueda.  El tercer parámetro es un puntero al elemento de matriz que se va a comparar con la clave.  
  
 `context`  
 Un puntero a un objeto que se puede tener acceso en la función de comparación.  
  
## Valor devuelto  
 Si se encuentra la clave, `_lfind_s` devuelve un puntero al elemento de matriz en `base` que coincide con `key`.  Si no se encuentra la clave, `_lfind_s` devuelve `NULL`.  
  
 Si los parámetros no válidos se pasan a la función, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `NULL`.  
  
### Condiciones de error  
  
|clave|base|compare|num|size|errno|  
|-----------|----------|-------------|---------|----------|-----------|  
|`NULL`|any|any|any|any|`EINVAL`|  
|any|`NULL`|any|\!\= 0|any|`EINVAL`|  
|any|any|any|any|cero|`EINVAL`|  
|any|any|`NULL`|an|any|`EINVAL`|  
  
## Comentarios  
 La función de `_lfind_s` realiza una búsqueda lineal por valor `key` en una matriz de elementos de `num` , cada uno de los bytes de `width` .  A diferencia de `bsearch_s`, `_lfind_s` no requiere una matriz ajustar su tamaño.  El argumento de `base` es un puntero a la base de la matriz que se buscará.  El argumento de `compare` es un puntero a una rutina usuario\- proporcionada que compara dos elementos de matriz y después devuelve un valor que especifica la relación.  `_lfind_s` llama a la rutina de `compare` una o más veces durante la búsqueda, pasando el puntero de `context` y punteros de dos elementos de la matriz en cada llamada.  La rutina de `compare` debe comparar elementos devuelve cero \(significa que los elementos son diferentes\) o 0 \(indican los elementos sea idéntico\).  
  
 `_lfind_s` es similar a `_lfind` salvo la adición del puntero de `context` a los argumentos de la función de comparación y la lista de parámetros de la función.  El puntero de `context` puede ser útil si la estructura de datos que se busca es parte de un objeto y la función de `compare` necesita tener acceso a los miembros del objeto.  La función de `compare` puede convertir el puntero vacío en el tipo de objeto adecuado y tener acceso a los miembros de ese objeto.  La adición del parámetro de `context` crea `_lfind_s` más seguro porque el contexto adicional se puede utilizar para evitar los errores de reentrada asociados al uso de variables estáticas que los datos estén disponibles para la función de `compare` .  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_lfind_s`|\<search.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## Ejemplo  
  
```  
// crt_lfind_s.cpp  
// This program uses _lfind_s to search a string array,  
// passing a locale as the context.  
// compile with: /EHsc  
#include <stdlib.h>  
#include <stdio.h>  
#include <search.h>  
#include <process.h>  
#include <locale.h>  
#include <locale>  
#include <windows.h>  
using namespace std;  
  
// The sort order is dependent on the code page.  Use 'chcp' at the  
// command line to change the codepage.  When executing this application,  
// the command prompt codepage must match the codepage used here:  
  
#define CODEPAGE_850  
  
#ifdef CODEPAGE_850  
// Codepage 850 is the OEM codepage used by the command line,  
// so \x00e1 is the German Sharp S  
  
char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",  
                   "weit" };  
  
#define GERMAN_LOCALE "German_Germany.850"  
  
#endif  
  
#ifdef CODEPAGE_1252  
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df  
   // for the German Sharp S  
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",  
                   "weit" };  
  
#define GERMAN_LOCALE "German_Germany.1252"  
  
#endif  
  
// The context parameter lets you create a more generic compare.  
// Without this parameter, you would have stored the locale in a  
// static variable, thus making it vulnerable to thread conflicts  
// (if this were a multithreaded program).  
  
int compare( void *pvlocale, const void *str1, const void *str2)  
{  
    char *s1 = *(char**)str1;  
    char *s2 = *(char**)str2;  
  
    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));  
  
    return use_facet< collate<char> >(loc).compare(  
       s1, s1+strlen(s1),  
       s2, s2+strlen(s2) );  
}  
  
void find_it( char *key, char *array[], unsigned int num, locale &loc )  
{  
   char **result = (char **)_lfind_s( &key, array,   
                      &num, sizeof(char *), compare, &loc );  
   if( result )  
      printf( "%s found\n", *result );  
   else  
      printf( "%s not found\n", key );  
}  
  
int main( )  
{  
   find_it( "weit", array1, sizeof(array1)/sizeof(char*), locale(GERMAN_LOCALE) );  
}  
```  
  
  **weit encontrado**   
## Equivalente en .NET Framework  
 <xref:System.Collections.ArrayList.Contains%2A>  
  
## Vea también  
 [Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch\_s](../../c-runtime-library/reference/bsearch-s.md)   
 [\_lsearch\_s](../../c-runtime-library/reference/lsearch-s.md)   
 [qsort\_s](../../c-runtime-library/reference/qsort-s.md)   
 [\_lfind](../../c-runtime-library/reference/lfind.md)