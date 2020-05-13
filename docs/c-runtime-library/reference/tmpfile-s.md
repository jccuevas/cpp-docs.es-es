---
title: tmpfile_s
ms.date: 4/2/2020
api_name:
- tmpfile_s
- _o_tmpfile_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tmpfile_s
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
ms.openlocfilehash: 48c599887a8a903d52c7dcd46b98046119c9d3ad
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919927"
---
# <a name="tmpfile_s"></a>tmpfile_s

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

|*pFilePtr*|**Valor devuelto**|**Contenido de**  *pFilePtr*|
|----------------|----------------------|---------------------------------|
|**ACEPTA**|**EINVAL**|no cambia|

Si se produce el error de validación de parámetros anterior, se invoca al controlador de parámetros no válidos, tal como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y el valor devuelto es **EINVAL**.

## <a name="remarks"></a>Observaciones

La función **tmpfile_s** crea un archivo temporal y coloca un puntero a ese flujo en el argumento *pFilePtr* . El archivo temporal se crea en el directorio raíz. Para crear un archivo temporal en un directorio que no sea el raíz, use [tmpnam_s](tmpnam-s-wtmpnam-s.md) o [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) junto con [fopen](fopen-wfopen.md).

Si no se puede abrir el archivo, **tmpfile_s** escribe **null** en el parámetro *pFilePtr* . Este archivo temporal se elimina automáticamente cuando se cierra el archivo, cuando el programa finaliza con normalidad o cuando se llama a **_rmtmp** , suponiendo que el directorio de trabajo actual no cambia. El archivo temporal se abre en modo **w + b** (lectura y escritura binaria).

Se puede producir un error si se intentan más de **TMP_MAX_S** (consulte stdio. H) llama a con **tmpfile_s**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**tmpfile_s**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

> [!NOTE]
> Este ejemplo puede requerir privilegios administrativos para ejecutarse en Windows.

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

## <a name="see-also"></a>Consulta también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
