---
title: tmpfile_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- tmpfile_s
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
- tmpfile_s
dev_langs:
- C++
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 04ccc149a214ccad7007ef140e87a5c20986b343
ms.lasthandoff: 02/24/2017

---
# <a name="tmpfiles"></a>tmpfile_s
Crea un archivo temporal. Es una versión de [tmpfile](../../c-runtime-library/reference/tmpfile.md) con mejoras de seguridad, como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t tmpfile_s(  
   FILE** pFilePtr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [out] `pFilePtr`  
 Dirección de un puntero para almacenar la dirección del puntero generado a un flujo.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve 0 si se ejecuta correctamente; devuelve un código de error si se produce un error.  
  
### <a name="error-conditions"></a>Condiciones de error  
  
|`pFilePtr`|**Valor devuelto**|**Contenido de** `pFilePtr`|  
|----------------|----------------------|---------------------------------|  
|`NULL`|`EINVAL`|no cambia|  
  
 Si se produce el error de validación de parámetros anterior, se invoca al controlador de parámetros no válidos, tal como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EINVAL` y el valor devuelto es `EINVAL`.  
  
## <a name="remarks"></a>Comentarios  
 La función `tmpfile_s` crea un archivo temporal y coloca un puntero a ese flujo en el argumento `pFilePtr`. El archivo temporal se crea en el directorio raíz. Para crear un archivo temporal en un directorio que no sea el raíz, use [tmpnam_s](../../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md) o [tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) junto con [fopen](../../c-runtime-library/reference/fopen-wfopen.md).  
  
 Si no se puede abrir el archivo, `tmpfile_s` escribe `NULL` en el parámetro `pFilePtr`. Este archivo temporal se elimina automáticamente cuando se cierra el archivo, cuando el programa finaliza normalmente o cuando se llama a `_rmtmp`, siempre que no cambie el directorio de trabajo actual. El archivo temporal se abre en modo `w+b` (lectura y escritura binario).  
  
 Se puede producir un error al intentar más de `TMP_MAX_S` llamadas (vea STDIO.H) con `tmpfile_s.`  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`tmpfile_s`|\<stdio.h>|  
  
 Para obtener información adicional de compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
  
> [!NOTE]
>  Este ejemplo exige privilegios administrativos para ejecutarse en Windows Vista.  
  
```  
// crt_tmpfile_s.c  
// This program uses tmpfile_s to create a  
// temporary file, then deletes this file with _rmtmp.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char tempstring[] = "String to be written";  
   int  i;  
   errno_t err;  
  
   // Create temporary files.  
   for( i = 1; i <= 3; i++ )  
   {  
      err = tmpfile_s(&stream);  
      if( err )  
         perror( "Could not open new temporary file\n" );  
      else  
         printf( "Temporary file %d was created\n", i );  
   }  
  
   // Remove temporary files.  
   printf( "%d temporary files deleted\n", _rmtmp() );  
}  
```  
  
```Output  
Temporary file 1 was created  
Temporary file 2 was created  
Temporary file 3 was created  
3 temporary files deleted  
```  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [_rmtmp](../../c-runtime-library/reference/rmtmp.md)   
 [_tempnam, _wtempnam, tmpnam, _wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)
