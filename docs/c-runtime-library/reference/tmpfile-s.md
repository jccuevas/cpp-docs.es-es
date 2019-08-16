---
title: tmpfile_s
ms.date: 11/04/2016
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
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
ms.openlocfilehash: 341e1c8ed6dd20ec7e6a3d71999fb365e45e614a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155581"
---
# <a name="tmpfiles"></a>tmpfile_s

Crea un archivo temporal. Es una versión de [tmpfile](tmpfile.md) con mejoras de seguridad, como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t tmpfile_s(
   FILE** pFilePtr
);
```

### <a name="parameters"></a>Parámetros

*pFilePtr*<br/>
Dirección de un puntero para almacenar la dirección del puntero generado a un flujo.

## <a name="return-value"></a>Valor devuelto

Devuelve 0 si se ejecuta correctamente; devuelve un código de error si se produce un error.

### <a name="error-conditions"></a>Condiciones de error

|*pFilePtr*|**Valor devuelto**|**Contenido de***pFilePtr*|
|----------------|----------------------|---------------------------------|
|**NULL**|**EINVAL**|no cambia|

Si se produce el error de validación de parámetros anterior, se invoca al controlador de parámetros no válidos, tal como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y el valor devuelto es **EINVAL**.

## <a name="remarks"></a>Comentarios

El **tmpfile_s** función crea un archivo temporal y coloca un puntero a ese flujo en el *pFilePtr* argumento. El archivo temporal se crea en el directorio raíz. Para crear un archivo temporal en un directorio que no sea el raíz, use [tmpnam_s](tmpnam-s-wtmpnam-s.md) o [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) junto con [fopen](fopen-wfopen.md).

Si no se puede abrir el archivo, **tmpfile_s** escribe **NULL** a la *pFilePtr* parámetro. Este archivo temporal se elimina automáticamente cuando se cierra el archivo, cuando el programa finaliza normalmente o cuando **_rmtmp** se llama, suponiendo que no cambie el directorio de trabajo actual. Se abre el archivo temporal en **w + b** modo (lectura/escritura binario).

Error puede producirse si intenta más de **TMP_MAX_S** (consulte STDIO. H) llamadas con **tmpfile_s**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**tmpfile_s**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

> [!NOTE]
> En este ejemplo puede requerir privilegios administrativos para ejecutarse en Windows.

```C
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

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
