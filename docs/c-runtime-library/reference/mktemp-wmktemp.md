---
title: _mktemp, _wmktemp | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wmktemp
- _mktemp
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tmktemp
- wmktemp
- tmktemp
- _wmktemp
- _mktemp
dev_langs:
- C++
helpviewer_keywords:
- _wmktemp function
- _mktemp function
- files [C++], temporary
- tmktemp function
- _tmktemp function
- wmktemp function
- mktemp function
- temporary files [C++]
ms.assetid: 055eb539-a8c2-4a7d-be54-f5b6d1eb5c85
caps.latest.revision: 25
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 1e56ba6f238c62a220966701e7b1ced1dd2ec4ea
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="mktemp-wmktemp"></a>_mktemp, _wmktemp
Crea un nombre de archivo único. Hay disponibles versiones más seguras de estas funciones; vea [_mktemp_s, _wmktemp_s](../../c-runtime-library/reference/mktemp-s-wmktemp-s.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
char *_mktemp(  
   char *template   
);  
wchar_t *_wmktemp(  
   wchar_t *template   
);  
template <size_t size>  
char *_mktemp(  
   char (&template)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_wmktemp(  
   wchar_t (&template)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parámetros  
 `template`  
 Patrón de nombre de archivo.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada una de estas funciones devuelve un puntero a la plantilla modificada. La función devuelve `NULL` si `template` es incorrecto o si no se pueden crear más nombres únicos desde la plantilla especificada.  
  
## <a name="remarks"></a>Comentarios  
 La función `_mktemp` crea un nombre de archivo único modificando el argumento `template`. `_mktemp` controla automáticamente los argumentos de cadenas de caracteres multibyte según corresponda, reconociendo las secuencias de caracteres multibyte según la página de códigos multibyte que usa actualmente el sistema en tiempo de ejecución. `_wmktemp` es una versión con caracteres anchos de `_mktemp`; el argumento y el valor devuelto de `_wmktemp` son cadenas de caracteres anchos. `_wmktemp` y `_mktemp` se comportan de manera idéntica, salvo que `_wmktemp` no controla las cadenas de caracteres multibyte.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tmktemp`|`_mktemp`|`_mktemp`|`_wmktemp`|  
  
 El `template` argumento tiene la forma `base` *XXXXXX*, donde `base` es la parte del nombre de archivo nuevo que suministre y cada X es un marcador de posición de un carácter proporcionado por `_mktemp`. Cada marcador de posición de `template` debe ser una X mayúscula. `_mktemp` conserva `base` y reemplaza la primera X final por un carácter alfabético. `_mktemp` reemplaza las siguientes X finales por un valor de cinco dígitos. Este valor es un número único que identifica el proceso al que se llama o, en programas multiproceso, el subproceso al que se llama.  
  
 Cada llamada correcta a `_mktemp` modifica `template`. En cada llamada posterior realizada desde el mismo proceso o subproceso con el mismo argumento `template`, `_mktemp` busca nombres de archivo que coincidan con los nombres devueltos por `_mktemp` en las llamadas anteriores. Si no existe ningún archivo para un nombre concreto, `_mktemp` devuelve dicho nombre. Si existen archivos de todos los nombres devueltos previamente, `_mktemp` crea un nombre nuevo sustituyendo el carácter alfabético que emplea en el nombre devuelto anteriormente por la siguiente letra minúscula disponible (en orden, de la «a» a la «z»). Por ejemplo, si `base` es:  
  
```  
fn  
```  
  
 y el valor de cinco dígitos proporcionado por `_mktemp` es 12345, el primer nombre devuelto es:  
  
```  
fna12345  
```  
  
 Si este nombre se usa para crear el archivo FNA12345 y el archivo todavía existe, el siguiente nombre devuelto en una llamada desde el mismo proceso o subproceso con el mismo `base` para `template` es:  
  
```  
fnb12345  
```  
  
 Si FNA12345 no existe, el siguiente nombre devuelto vuelve a ser:  
  
```  
fna12345  
```  
  
 `_mktemp` puede crear un máximo de 26 nombres de archivo únicos para cualquier combinación de valores de base y de plantilla. Por lo tanto, FNZ12345 es el último nombre de archivo único que `_mktemp` puede crear para los valores `base` y `template` usados en este ejemplo.  
  
 En caso de error, se establece `errno`. Si `template` tiene un formato no válido (por ejemplo, menos de 6 X), `errno` se establece en `EINVAL`. Si `_mktemp` no puede crear un nombre único porque ya existen los 26 nombres de archivo posibles, `_mktemp` establece la plantilla en una cadena vacía y devuelve `EEXIST`.  
  
 En C++, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones. Para más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_mktemp`|\<io.h>|  
|`_wmktemp`|\<io.h> o \<wchar.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_mktemp.c  
// compile with: /W3  
/* The program uses _mktemp to create  
 * unique filenames. It opens each filename  
 * to ensure that the next name is unique.  
 */  
  
#include <io.h>  
#include <string.h>  
#include <stdio.h>  
#include <errno.h>  
  
char *template = "fnXXXXXX";  
char *result;  
char names[27][9];  
  
int main( void )  
{  
   int i;  
   FILE *fp;  
  
   for( i = 0; i < 27; i++ )  
   {  
      strcpy_s( names[i], sizeof( names[i] ), template );  
      /* Attempt to find a unique filename: */  
      result = _mktemp( names[i] );  // C4996  
      // Note: _mktemp is deprecated; consider using _mktemp_s instead  
      if( result == NULL )  
      {  
         printf( "Problem creating the template\n" );  
         if (errno == EINVAL)  
         {  
             printf( "Bad parameter\n");  
         }  
         else if (errno == EEXIST)  
         {  
             printf( "Out of unique filenames\n");   
         }  
      }  
      else  
      {  
         fopen_s( &fp, result, "w" );  
         if( fp != NULL )  
            printf( "Unique filename is %s\n", result );  
         else  
            printf( "Cannot open %s\n", result );  
         fclose( fp );  
      }  
   }  
}  
```  
  
```Output  
Unique filename is fna03912  
Unique filename is fnb03912  
Unique filename is fnc03912  
Unique filename is fnd03912  
Unique filename is fne03912  
Unique filename is fnf03912  
Unique filename is fng03912  
Unique filename is fnh03912  
Unique filename is fni03912  
Unique filename is fnj03912  
Unique filename is fnk03912  
Unique filename is fnl03912  
Unique filename is fnm03912  
Unique filename is fnn03912  
Unique filename is fno03912  
Unique filename is fnp03912  
Unique filename is fnq03912  
Unique filename is fnr03912  
Unique filename is fns03912  
Unique filename is fnt03912  
Unique filename is fnu03912  
Unique filename is fnv03912  
Unique filename is fnw03912  
Unique filename is fnx03912  
Unique filename is fny03912  
Unique filename is fnz03912  
Problem creating the template.  
Out of unique filenames.  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [fopen, _wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [_getpid](../../c-runtime-library/reference/getpid.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [_tempnam, _wtempnam, tmpnam, _wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)   
 [tmpfile](../../c-runtime-library/reference/tmpfile.md)
