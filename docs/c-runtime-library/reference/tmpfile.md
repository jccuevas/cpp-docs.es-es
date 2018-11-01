---
title: tmpfile
ms.date: 11/04/2016
apiname:
- tmpfile
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
- tmpfile
helpviewer_keywords:
- temporary files
- tmpfile function
- temporary files, creating
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
ms.openlocfilehash: 98afcb7a3e04a96a1b08bc1b975634153e550839
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530330"
---
# <a name="tmpfile"></a>tmpfile

Crea un archivo temporal. Esta función está en desuso, ya que existe una versión más segura; vea [tmpfile_s](tmpfile-s.md).

## <a name="syntax"></a>Sintaxis

```C
FILE *tmpfile( void );
```

## <a name="return-value"></a>Valor devuelto

Si es correcto, **tmpfile** devuelve un puntero de la secuencia. De lo contrario, devuelve un **NULL** puntero.

## <a name="remarks"></a>Comentarios

El **tmpfile** función crea un archivo temporal y devuelve un puntero a ese flujo. El archivo temporal se crea en el directorio raíz. Para crear un archivo temporal en un directorio que no sea el raíz, use [tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) o [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) junto con [fopen](fopen-wfopen.md).

Si no se puede abrir el archivo, **tmpfile** devuelve un **NULL** puntero. Este archivo temporal se elimina automáticamente cuando se cierra el archivo, cuando el programa finaliza normalmente o cuando **_rmtmp** se llama, suponiendo que no cambie el directorio de trabajo actual. Se abre el archivo temporal en **w + b** modo (lectura/escritura binario).

Error puede producirse si intenta más de TMP_MAX (consulte STDIO. H) llamadas con **tmpfile**.

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
