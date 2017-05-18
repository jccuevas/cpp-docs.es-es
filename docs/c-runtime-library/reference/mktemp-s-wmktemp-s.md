---
title: _mktemp_s, _wmktemp_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mktemp_s
- _wmktemp_s
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
apitype: DLLExport
f1_keywords:
- wmktemp_s
- mktemp_s
- _mktemp_s
- _wmktemp_s
dev_langs:
- C++
helpviewer_keywords:
- _tmktemp_s function
- mktemp_s function
- _wmktemp_s function
- _mktemp_s function
- files [C++], temporary
- tmktemp_s function
- wmktemp_s function
- temporary files [C++]
ms.assetid: 92a7e269-7f3d-4c71-bad6-14bc827a451d
caps.latest.revision: 23
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 6231031dd0bbc5b455e3555731f711ee7de971e7
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="mktemps-wmktemps"></a>_mktemp_s, _wmktemp_s
Crea un nombre de archivo único. Se trata de versiones de [_mktemp, _wmktemp](../../c-runtime-library/reference/mktemp-wmktemp.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t _mktemp_s(  
   char *template,  
   size_t sizeInChars  
);  
errno_t _wmktemp_s(  
   wchar_t *template,  
   size_t sizeInChars  
);  
template <size_t size>  
errno_t _mktemp_s(  
   char (&template)[size]  
); // C++ only  
template <size_t size>  
errno_t _wmktemp_s(  
   wchar_t (&template)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parámetros  
 `template`  
 Patrón de nombre de archivo.  
  
 `sizeInChars`  
 Tamaño del búfer en caracteres de byte único en `_mktemp_s`; caracteres anchos en `_wmktemp_s`, incluido el terminador nulo.  
  
## <a name="return-value"></a>Valor devuelto  
 Ambas funciones devuelven cero si se realizan correctamente o un código de error en caso de error.  
  
### <a name="error-conditions"></a>Condiciones de error  
  
|`template`|`sizeInChars`|**valor devuelto**|**nuevo valor en la plantilla**|  
|----------------|-------------------|----------------------|-------------------------------|  
|`NULL`|cualquiera|`EINVAL`|`NULL`|  
|Formato incorrecto (vea la sección `Remarks` para ver el formato correcto)|cualquiera|`EINVAL`|cadena vacía|  
|any|<= número de X|`EINVAL`|cadena vacía|  
  
 Si se da alguna de las condiciones de error anteriores, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `EINVAL`.  
  
## <a name="remarks"></a>Comentarios  
 La función `_mktemp_s` crea un nombre de archivo único modificando el argumento `template`. Así, después de la llamada, el puntero `template` apunta a una cadena que contiene el nuevo nombre de archivo. `_mktemp_s` controla automáticamente los argumentos de cadenas de caracteres multibyte según corresponda, reconociendo las secuencias de caracteres multibyte según la página de códigos multibyte que usa actualmente el sistema en tiempo de ejecución. `_wmktemp_s` es una versión con caracteres anchos de `_mktemp_s`; el argumento de `_wmktemp_s` es una cadena de caracteres anchos. `_wmktemp_s` y `_mktemp_s` se comportan de manera idéntica, salvo que `_wmktemp_s` no controla las cadenas de caracteres multibyte.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tmktemp_s`|`_mktemp_s`|`_mktemp_s`|`_wmktemp_s`|  
  
 El argumento `template` tiene el formato `baseXXXXXX`, donde `base` es la parte del nuevo nombre de archivo proporcionado y cada X es un marcador de posición de un carácter proporcionado por `_mktemp_s`. Cada marcador de posición de `template` debe ser una X mayúscula. `_mktemp_s` conserva `base` y reemplaza la primera X final por un carácter alfabético. `_mktemp_s` reemplaza las siguientes X finales por un valor de cinco dígitos. Este valor es un número único que identifica el proceso al que se llama o, en programas multiproceso, el subproceso al que se llama.  
  
 Cada llamada correcta a `_mktemp_s` modifica `template`. En cada llamada posterior realizada desde el mismo proceso o subproceso con el mismo argumento `template`, `_mktemp_s` busca nombres de archivo que coincidan con los nombres devueltos por `_mktemp_s` en las llamadas anteriores. Si no existe ningún archivo para un nombre concreto, `_mktemp_s` devuelve dicho nombre. Si existen archivos de todos los nombres devueltos previamente, `_mktemp_s` crea un nombre nuevo sustituyendo el carácter alfabético que emplea en el nombre devuelto anteriormente por la siguiente letra minúscula disponible (en orden, de la «a» a la «z»). Por ejemplo, si `base` es:  
  
```  
fn  
```  
  
 y el valor de cinco dígitos proporcionado por `_mktemp_s` es 12345, el primer nombre devuelto es:  
  
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
  
 `_mktemp_s` puede crear un máximo de 26 nombres de archivo únicos para cualquier combinación de valores de base y de plantilla. Por lo tanto, FNZ12345 es el último nombre de archivo único que `_mktemp_s` puede crear para los valores `base` y `template` usados en este ejemplo.  
  
 En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_mktemp_s`|\<io.h>|  
|`_wmktemp_s`|\<io.h> o \<wchar.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_mktemp_s.cpp  
/* The program uses _mktemp to create  
 * five unique filenames. It opens each filename  
 * to ensure that the next name is unique.  
 */  
  
#include <io.h>  
#include <string.h>  
#include <stdio.h>  
  
char *fnTemplate = "fnXXXXXX";  
char names[5][9];  
  
int main()  
{  
   int i, err, sizeInChars;  
   FILE *fp;  
  
   for( i = 0; i < 5; i++ )  
   {  
      strcpy_s( names[i], sizeof(names[i]), fnTemplate );  
      /* Get the size of the string and add one for the null terminator.*/  
      sizeInChars = strnlen(names[i], 9) + 1;  
      /* Attempt to find a unique filename: */  
      err = _mktemp_s( names[i], sizeInChars );  
      if( err != 0 )  
         printf( "Problem creating the template" );  
      else  
      {  
         if( fopen_s( &fp, names[i], "w" ) == 0 )  
            printf( "Unique filename is %s\n", names[i] );  
         else  
            printf( "Cannot open %s\n", names[i] );  
         fclose( fp );  
      }  
   }  
  
   return 0;  
}  
```  
  
## <a name="sample-output"></a>Resultados del ejemplo  
  
```  
Unique filename is fna03188  
Unique filename is fnb03188  
Unique filename is fnc03188  
Unique filename is fnd03188  
Unique filename is fne03188  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [fopen, _wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [_getpid](../../c-runtime-library/reference/getpid.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [_tempnam, _wtempnam, tmpnam, _wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)   
 [tmpfile_s](../../c-runtime-library/reference/tmpfile-s.md)
