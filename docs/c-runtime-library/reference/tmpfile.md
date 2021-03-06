---
title: tmpfile
ms.date: 11/04/2016
api_name:
- tmpfile
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tmpfile
helpviewer_keywords:
- temporary files
- tmpfile function
- temporary files, creating
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
ms.openlocfilehash: f58c23050fe89f84f283c3784a7c0cee72637bf2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957543"
---
# <a name="tmpfile"></a>tmpfile

Crea un archivo temporal. Esta función está en desuso, ya que existe una versión más segura; vea [tmpfile_s](tmpfile-s.md).

## <a name="syntax"></a>Sintaxis

```C
FILE *tmpfile( void );
```

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, **tmpfile** devuelve un puntero de secuencia. De lo contrario, devuelve un puntero **nulo** .

## <a name="remarks"></a>Comentarios

La función **tmpfile** crea un archivo temporal y devuelve un puntero a ese flujo. El archivo temporal se crea en el directorio raíz. Para crear un archivo temporal en un directorio que no sea el raíz, use [tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) o [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) junto con [fopen](fopen-wfopen.md).

Si no se puede abrir el archivo, **tmpfile** devuelve un puntero **nulo** . Este archivo temporal se elimina automáticamente cuando se cierra el archivo, cuando el programa finaliza con normalidad o cuando se llama a **_rmtmp** , suponiendo que el directorio de trabajo actual no cambia. El archivo temporal se abre en modo **w + b** (lectura y escritura binaria).

Se puede producir un error si se intenta más de TMP_MAX (consulte STDIO. H) llama a con **tmpfile**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**tmpfile**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

> [!NOTE]
> Este ejemplo exige privilegios administrativos para ejecutarse en Windows Vista.

```C
// crt_tmpfile.c
// compile with: /W3
// This program uses tmpfile to create a
// temporary file, then deletes this file with _rmtmp.
#include <stdio.h>

int main( void )
{
   FILE *stream;
   int  i;

   // Create temporary files.
   for( i = 1; i <= 3; i++ )
   {
      if( (stream = tmpfile()) == NULL ) // C4996
      // Note: tmpfile is deprecated; consider using tmpfile_s instead
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

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
