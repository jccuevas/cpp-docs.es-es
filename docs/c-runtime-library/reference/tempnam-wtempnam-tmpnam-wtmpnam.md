---
title: _tempnam, _wtempnam, tmpnam, _wtmpnam | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wtempnam
- _wtmpnam
- tmpnam
- _tempnam
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
- wtempnam
- _wtmpnam
- wtmpnam
- tmpnam
- _wtempnam
- _tempnam
dev_langs:
- C++
helpviewer_keywords:
- wtempnam function
- file names [C++], creating temporary
- _tempnam function
- ttmpnam function
- tmpnam function
- tempnam function
- wtmpnam function
- temporary files, creating
- file names [C++], temporary
- _ttmpnam function
- _wtmpnam function
- _wtempnam function
ms.assetid: 3ce75f0f-5e30-42a6-9791-8d7cbfe70fca
caps.latest.revision: 20
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
ms.openlocfilehash: 0600d44b2b87ed3bb56e7d1c64fffd762e77aff2
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="tempnam-wtempnam-tmpnam-wtmpnam"></a>_tempnam, _wtempnam, tmpnam, _wtmpnam
Genere nombres que se puedan usar para crear archivos temporales. Hay disponibles versiones más seguras de algunas de estas funciones; vea [tmpnam_s, _wtmpnam_s](../../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
char *_tempnam(  
   const char *dir,  
   const char *prefix   
);  
wchar_t *_wtempnam(  
   const wchar_t *dir,  
   const wchar_t *prefix   
);  
char *tmpnam(  
   char *str   
);  
wchar_t *_wtmpnam(  
   wchar_t *str   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `prefix`  
 Cadena que se va a anteponer a los nombres devueltos por `_tempnam`.  
  
 `dir`  
 Ruta de acceso que se usa en el nombre de archivo si no hay variable de entorno TMP, o si TMP no es un directorio válido.  
  
 `str`  
 Puntero que va a conservar el nombre generado, que será idéntico al nombre devuelto por la función. Se trata de una manera cómoda de guardar el nombre generado.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada una de estas funciones devuelve un puntero al nombre generado o `NULL` si se produce un error. Error puede ocurrir si se intenta superar `TMP_MAX` (vea STDIO. (H) llamadas con `tmpnam` o si utiliza `_tempnam` y no hay un nombre de directorio no válido especificado en la variable de entorno TMP y en el `dir` parámetro.  
  
> [!NOTE]
>  Los punteros devueltos por `tmpnam` y `_wtmpnam` apuntan a búferes estáticos internos. No debe llamarse a [free](../../c-runtime-library/reference/free.md) para desasignar esos punteros. Es necesario llamar a `free` en el caso de los punteros asignados por `_tempnam` y `_wtempnam`.  
  
## <a name="remarks"></a>Comentarios  
 Cada una de estas funciones devuelve el nombre de un archivo que no existe en este momento. `tmpnam` devuelve un nombre único en el directorio de trabajo actual y `_tempnam` permite generar un nombre único en un directorio distinto al actual. Tenga en cuenta que cuando un nombre de archivo va precedido por una barra diagonal inversa sin información de ruta de acceso, como \fname21, esto indica que el nombre es válido para el directorio de trabajo actual.  
  
 En el caso de `tmpnam`, puede almacenar este nombre de archivo generado en `str`. Si `str` es `NULL`, `tmpnam` deja el resultado en un búfer estático interno. Por lo tanto, las siguientes llamadas destruyen este valor. El nombre generado por `tmpnam` consta de un nombre de archivo generado por el programa y, tras la primera llamada a `tmpnam`, de una extensión de archivo de números secuenciales en base 32 (.1-.vvu cuando `TMP_MAX` en STDIO.H es 32.767).  
  
 `_tempnam` generará un nombre de archivo único para un directorio elegido por las reglas siguientes:  
  
-   Si la variable de entorno TMP está definida y establecida en un nombre de directorio válido, se generarán nombres de archivo únicos para el directorio especificado por TMP.  
  
-   Si la variable de entorno TMP no está definida o está establecida en el nombre de un directorio que no existe, `_tempnam` usará el parámetro `dir` como ruta de acceso para la que generar nombres únicos.  
  
-   Si la variable de entorno TMP no está definida o está establecida en el nombre de un directorio que no existe y `dir` es `NULL` o está establecido en el nombre de un directorio que no existe, `_tempnam` usará el directorio de trabajo actual para generar nombres únicos. En este momento, si TMP y `dir` especifican nombres de directorios que no existen, se produce un error al llamar a la función `_tempnam`.  
  
 El nombre devuelto por `_tempnam` será una concatenación de `prefix` y un número secuencial que se combinarán para crear un nombre de archivo único para el directorio especificado. `_tempnam` genera nombres de archivo sin extensión. `_tempnam` usa [malloc](../../c-runtime-library/reference/malloc.md) para asignar espacio para el nombre de archivo; el programa es responsable de liberar este espacio cuando ya no es necesario.  
  
 `_tempnam` y `tmpnam` controlan automáticamente argumentos de cadena de caracteres multibyte como sea necesario, reconociendo las secuencias de caracteres multibyte en función de la página de códigos OEM obtenida del sistema operativo. `_wtempnam` es una versión con caracteres anchos de `_tempnam`; los argumentos y el valor devuelto de `_wtempnam` son cadenas de caracteres anchos. `_wtempnam` y `_tempnam` se comportan de manera idéntica, salvo que `_wtempnam` no controla cadenas de caracteres multibyte. `_wtmpnam` es una versión con caracteres anchos de `tmpnam`; el argumento y el valor devuelto de `_wtmpnam` son cadenas de caracteres anchos. `_wtmpnam` y `tmpnam` se comportan de manera idéntica, salvo que `_wtmpnam` no controla cadenas de caracteres multibyte.  
  
 Si `_DEBUG` y `_CRTDBG_MAP_ALLOC` están definidos, `_tempnam` y `_wtempnam` se sustituyen por llamadas a [_tempnam_dbg y _wtempnam_dbg](../../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md).  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ttmpnam`|`tmpnam`|`tmpnam`|`_wtmpnam`|  
|`_ttempnam`|`_tempnam`|`_tempnam`|`_wtempnam`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_tempnam`|\<stdio.h>|  
|`_wtempnam`, `_wtmpnam`|\<stdio.h> o \<wchar.h>|  
|`tmpnam`|\<stdio.h>|  
  
 Para obtener información adicional de compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_tempnam.c  
// compile with: /W3  
// This program uses tmpnam to create a unique filename in the  
// current working directory, then uses _tempnam to create   
// a unique filename with a prefix of stq.   
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{     
   char* name1 = NULL;  
   char* name2 = NULL;  
  
   // Create a temporary filename for the current working directory:   
   if( ( name1 = tmpnam( NULL ) ) != NULL ) // C4996  
   // Note: tmpnam is deprecated; consider using tmpnam_s instead  
      printf( "%s is safe to use as a temporary file.\n", name1 );  
   else  
      printf( "Cannot create a unique filename\n" );  
  
   // Create a temporary filename in temporary directory with the  
   // prefix "stq". The actual destination directory may vary  
   // depending on the state of the TMP environment variable and  
   // the global variable P_tmpdir.     
  
   if( ( name2 = _tempnam( "c:\\tmp", "stq" ) ) != NULL )  
      printf( "%s is safe to use as a temporary file.\n", name2 );   
   else  
      printf( "Cannot create a unique filename\n" );  
  
   // When name2 is no longer needed :     
   if(name2)  
     free(name2);  
  
}  
```  
  
```Output  
\s1gk. is safe to use as a temporary file.  
C:\DOCUME~1\user\LOCALS~1\Temp\2\stq2 is safe to use as a temporary file.  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [tmpfile](../../c-runtime-library/reference/tmpfile.md)   
 [tmpfile_s](../../c-runtime-library/reference/tmpfile-s.md)
