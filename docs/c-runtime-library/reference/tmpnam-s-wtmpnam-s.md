---
title: tmpnam_s, _wtmpnam_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- tmpnam_s
- _wtmpnam_s
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
- tmpnam_s
- _wtmpnam_s
- L_tmpnam_s
dev_langs:
- C++
helpviewer_keywords:
- tmpnam_s function
- file names [C++], creating temporary
- _wtmpnam_s function
- L_tmpnam_s constant
- temporary files, creating
- file names [C++], temporary
- wtmpnam_s function
ms.assetid: e70d76dc-49f5-4aee-bfa2-f1baa2bcd29f
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: c2a7276c8670bf0a3fd56ac8c0df111e82da16de
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="tmpnams-wtmpnams"></a>tmpnam_s, _wtmpnam_s
Genere nombres que se puedan usar para crear archivos temporales. Estas son versiones de [tmpnam y _wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) con mejoras de seguridad, como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t tmpnam_s(  
   char * str,  
   size_t sizeInChars   
);  
errno_t _wtmpnam_s(  
   wchar_t *str,  
   size_t sizeInChars   
);  
template <size_t size>  
errno_t tmpnam_s(  
   char (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _wtmpnam_s(  
   wchar_t (&str)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parámetros  
 [out] `str`  
 Puntero que va a contener el nombre generado.  
  
 [in] `sizeInChars`  
 Tamaño del búfer en caracteres.  
  
## <a name="return-value"></a>Valor devuelto  
 Ambas funciones devuelven 0 si se realizan correctamente o un número de error en caso contrario.  
  
### <a name="error-conditions"></a>Condiciones de error  
  
|||||  
|-|-|-|-|  
|`str`|`sizeInChars`|**Valor devuelto**|**Contenido de** `str`|  
|`NULL`|cualquiera|`EINVAL`|no modificado|  
|no `NULL` (apunta a la memoria válida)|demasiado corto|`ERANGE`|no modificado|  
  
 Si `str` es `NULL`, se invoca al controlador de parámetros no válidos, tal como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven `EINVAL`.  
  
## <a name="remarks"></a>Comentarios  
 Cada una de estas funciones devuelve el nombre de un archivo que no existe en este momento. `tmpnam_s` devuelve un nombre único en el directorio de trabajo actual. Tenga en cuenta que cuando un nombre de archivo va precedido por una barra diagonal inversa sin información de ruta de acceso, como \fname21, esto indica que el nombre es válido para el directorio de trabajo actual.  
  
 En el caso de `tmpnam_s`, puede almacenar este nombre de archivo generado en `str`. La longitud máxima de una cadena devuelta por `tmpnam_s` es `L_tmpnam_s`, definida en STDIO.H. Si `str` es `NULL`, `tmpnam_s` deja el resultado en un búfer estático interno. Por lo tanto, las siguientes llamadas destruyen este valor. El nombre generado por `tmpnam_s` consta de un nombre de archivo generado por el programa y, tras la primera llamada a `tmpnam_s`, de una extensión de archivo de números secuenciales en base 32 (.1-.1vvvvvu cuando `TMP_MAX_S` en STDIO.H es INT_MAX).  
  
 `tmpnam_s` controla automáticamente argumentos de cadena de caracteres multibyte como sea necesario, reconociendo las secuencias de caracteres multibyte en función de la página de códigos OEM obtenida del sistema operativo. `_wtmpnam_s` es una versión con caracteres anchos de `tmpnam_s`; el argumento y el valor devuelto de `_wtmpnam_s` son cadenas de caracteres anchos. `_wtmpnam_s` y `tmpnam_s` se comportan de manera idéntica, salvo que `_wtmpnam_s` no controla cadenas de caracteres multibyte.  
  
 En C++, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, consulte [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ttmpnam_s`|`tmpnam_s`|`tmpnam_s`|`_wtmpnam_s`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`tmpnam_s`|\<stdio.h>|  
|`_wtmpnam_s`|\<stdio.h> o \<wchar.h>|  
  
 Para obtener información adicional de compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_tmpnam_s.c  
// This program uses tmpnam_s to create a unique filename in the  
// current working directory.   
//  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{     
   char name1[L_tmpnam_s];  
   errno_t err;  
   int i;  
  
   for (i = 0; i < 15; i++)  
   {  
      err = tmpnam_s( name1, L_tmpnam_s );  
      if (err)  
      {  
         printf("Error occurred creating unique filename.\n");  
         exit(1);  
      }  
      else  
      {  
         printf( "%s is safe to use as a temporary file.\n", name1 );  
      }  
   }    
}  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [tmpfile_s](../../c-runtime-library/reference/tmpfile-s.md)
