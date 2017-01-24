---
title: "qsort_s | Microsoft Docs"
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
  - "qsort_s"
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
  - "qsort_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "matrices [C++], ordenar"
  - "qsort_s (función)"
  - "algoritmo de ordenación rápida"
  - "ordenar matrices"
ms.assetid: 6ee817b0-4408-4355-a5d4-6605e419ab91
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# qsort_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Realiza una ordenación rápida.  Una versión de [qsort](../../c-runtime-library/reference/qsort.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
void qsort_s(  
   void *base,  
   size_t num,  
   size_t width,  
   int (__cdecl *compare )(void *, const void *, const void *),  
   void * context  
);  
```  
  
#### Parámetros  
 `base`  
 Inicio de la matriz de destino.  
  
 `num`  
 Tamaño de la matriz de elementos.  
  
 `width`  
 Tamaño del elemento en bytes.  
  
 `compare`  
 Función de comparación.  El primer argumento es el puntero de `context` .  El segundo argumento es un puntero a `key` para la búsqueda.  El tercer argumento es un puntero al elemento de matriz que se va a comparar con `key`.  
  
 `context`  
 Un puntero a un contexto, que puede ser cualquier objeto al que `compare` rutinario necesite obtener acceso.  
  
## Comentarios  
 La función de `qsort_s` implementa un algoritmo de la rápido\- ordenación para ordenar una matriz de elementos de `num` , cada uno de los bytes de `width` .  El argumento `base` es un puntero a la base de la matriz que se ordenen.  `qsort_s` sobrescribe esta matriz con los elementos ordenados.  El argumento `compare` es un puntero a una rutina usuario\- proporcionada que compara dos elementos de matriz y devuelve un valor que especifica la relación.  `qsort_s` llama a la rutina de `compare` una o más veces durante la ordenación, pasando punteros a dos elementos de la matriz en cada llamada:  
  
```  
compare( context, (void *) & elem1, (void *) & elem2 );  
```  
  
 La rutina debe comparar los elementos y después devolver uno de los siguientes valores:  
  
|Valor devuelto|Descripción|  
|--------------------|-----------------|  
|\< 0|`elem1` es menor que `elem2`|  
|0|equivalente de`elem1` a `elem2`|  
|\> 0|`elem1` es mayor que `elem2`|  
  
 La matriz se ordena en sentido petición, definido por la función de comparación.  Para ordenar una matriz en orden descendente, invierta el sentido de “mayor que” y “menor que” en la función de comparación.  
  
 Si los parámetros no válidos se pasan a la función, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve y `errno` se establece en `EINVAL`.  Para obtener más información, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
### Condiciones de error  
  
|clave|base|compare|num|width|errno|  
|-----------|----------|-------------|---------|-----------|-----------|  
|`NULL`|any|any|any|any|`EINVAL`|  
|any|`NULL`|any|\!\= 0|any|`EINVAL`|  
|any|any|any|any|\<\= 0|`EINVAL`|  
|any|any|`NULL`|any|any|`EINVAL`|  
  
 `qsort_s` tiene el mismo comportamiento que `qsort` pero tiene el parámetro de `context` y establece `errno`.  Pasando un parámetro de `context` , las funciones de comparación pueden utilizar un puntero de objeto a la funcionalidad del objeto de acceso u otra información no accesible a través de un puntero de elemento.  La adición del parámetro de `context` crea `qsort_s`más seguro porque `context` se puede utilizar para evitar los errores de reentrada proporcionados mediante variables estáticas para incluir información compartida a disposición de la función de `compare` .  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`qsort_s`|\<stdlib.h y\> search.h \<\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
 **Bibliotecas:** Todas las versiones de [Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
 El siguiente ejemplo se muestra cómo utilizar el parámetro de `context` en función de `qsort_s`.  El parámetro de `context` facilita realizar ordenaciones segura para subprocesos.  En lugar de utilizar las variables estáticas que se deben sincronizar para garantizar la seguridad para subprocesos, pase otro parámetro de `context` en cada ordenada.  En este ejemplo, un objeto de la configuración regional se utiliza como parámetro de `context` .  
  
```  
// crt_qsort_s.cpp  
// compile with: /EHsc /MT  
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
// so \x00e1 is the German Sharp S in that codepage and \x00a4  
// is the n tilde.  
  
char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",  
                   "weit" };  
char *array2[] = { "Espa\x00a4ol", "Espa\x00a4" "a", "espantado" };  
char *array3[] = { "table", "tableux", "tablet" };  
  
#define GERMAN_LOCALE "German_Germany.850"  
#define SPANISH_LOCALE "Spanish_Spain.850"  
#define ENGLISH_LOCALE "English_US.850"  
  
#endif  
  
#ifdef CODEPAGE_1252  
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df  
   // for the German Sharp S and \x001f for the n tilde.  
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",  
                   "weit" };  
char *array2[] = { "Espa\x00f1ol", "Espa\x00f1" "a", "espantado" };  
char *array3[] = { "table", "tableux", "tablet" };  
  
#define GERMAN_LOCALE "German_Germany.1252"  
#define SPANISH_LOCALE "Spanish_Spain.1252"  
#define ENGLISH_LOCALE "English_US.1252"  
  
#endif  
  
// The context parameter lets you create a more generic compare.  
// Without this parameter, you would have stored the locale in a  
// static variable, thus making sort_array vulnerable to thread  
// conflicts.  
  
int compare( void *pvlocale, const void *str1, const void *str2)  
{  
    char s1[256];  
    char s2[256];  
    strcpy_s(s1, 256, *(char**)str1);  
    strcpy_s(s2, 256, *(char**)str2);  
    _strlwr_s( s1, sizeof(s1) );  
    _strlwr_s( s2, sizeof(s2) );  
  
    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));  
  
    return use_facet< collate<char> >(loc).compare(s1,   
       &s1[strlen(s1)], s2, &s2[strlen(s2)]);  
  
}  
  
void sort_array(char *array[], int num, locale &loc)  
{  
    qsort_s(array, num, sizeof(char*), compare, &loc);  
}  
  
void print_array(char *a[], int c)  
{  
   for (int i = 0; i < c; i++)  
     printf("%s ", a[i]);  
   printf("\n");  
  
}  
  
void sort_german(void * Dummy)  
{  
   sort_array(array1, 6, locale(GERMAN_LOCALE));  
}  
  
void sort_spanish(void * Dummy)  
{     
   sort_array(array2, 3, locale(SPANISH_LOCALE));       
}  
  
void sort_english(void * Dummy)  
{     
   sort_array(array3, 3, locale(ENGLISH_LOCALE));     
}  
  
int main( )  
{  
  
   int i;  
   HANDLE threads[3];  
  
   printf("Unsorted input:\n");  
   print_array(array1, 6);  
   print_array(array2, 3);  
   print_array(array3, 3);  
  
   // Create several threads that perform sorts in different  
   // languages at the same time.   
  
   threads[0] = reinterpret_cast<HANDLE>(  
                 _beginthread( sort_german , 0, NULL));  
   threads[1] = reinterpret_cast<HANDLE>(  
                 _beginthread( sort_spanish, 0, NULL));  
   threads[2] = reinterpret_cast<HANDLE>(  
                 _beginthread( sort_english, 0, NULL));  
  
   for (i = 0; i < 3; i++)  
   {  
      if (threads[i] == reinterpret_cast<HANDLE>(-1))  
      {  
         printf("Error creating threads.\n");  
         exit(1);  
      }  
   }  
  
   // Wait until all threads have terminated.  
   WaitForMultipleObjects(3, threads, true, INFINITE);  
  
   printf("Sorted output: \n");  
  
   print_array(array1, 6);  
   print_array(array2, 3);  
   print_array(array3, 3);  
  
}  
```  
  
## Resultados del ejemplo  
  
```  
Unsorted input:  
weiß weis annehmen weizen Zeit weit   
Español España espantado   
table tableux tablet   
Sorted output:   
annehmen weiß weis weit weizen Zeit   
España Español espantado   
table tablet tableux  
```  
  
## Equivalente en .NET Framework  
 <xref:System.Collections.ArrayList.Sort%2A>  
  
## Vea también  
 [Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch\_s](../../c-runtime-library/reference/bsearch-s.md)   
 [\_lsearch\_s](../../c-runtime-library/reference/lsearch-s.md)   
 [qsort](../../c-runtime-library/reference/qsort.md)