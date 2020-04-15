---
title: freopen_s, _wfreopen_s
ms.date: 4/2/2020
api_name:
- _wfreopen_s
- freopen_s
- _o__wfreopen_s
- _o_freopen_s
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- freopen_s
- _tfreopen_s
- _wfreopen_s
helpviewer_keywords:
- _tfreopen_s function
- _wfreopen_s function
- file pointers [C++], reassigning
- tfreopen_s function
- wfreopen_s function
- freopen_s function
ms.assetid: ad25a4da-6ad4-476b-a86d-660b221ca84d
ms.openlocfilehash: a24e34ead905d2f704bfbf4d829064c656272e97
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345917"
---
# <a name="freopen_s-_wfreopen_s"></a>freopen_s, _wfreopen_s

Reasigna un puntero de archivo. Estas versiones de [freopen, _wfreopen](freopen-wfreopen.md) incluyen mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t freopen(
   FILE** pFile,
   const char *path,
   const char *mode,
   FILE *stream
);
errno_t _wfreopen(
   FILE** pFile,
   const wchar_t *path,
   const wchar_t *mode,
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*pFile*<br/>
Puntero al puntero de archivo que la llamada va a proporcionar.

*path*<br/>
Ruta de acceso del nuevo archivo.

*Modo*<br/>
Tipo de acceso permitido.

*Corriente*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un código de error. Si se produce un error, el archivo original se cierra.

## <a name="remarks"></a>Observaciones

La función **freopen_s** cierra el archivo asociado actualmente a *la secuencia* y reasigna la *secuencia* al archivo especificado por *path*. **_wfreopen_s** es una versión de caracteres anchos de **_freopen_s;** los argumentos *de ruta* de acceso y *modo* para **_wfreopen_s** son cadenas de caracteres anchos. **_wfreopen_s** y **_freopen_s** comportarse de forma idéntica de lo contrario.

Si cualquiera de *pFile*, *path*, *mode*o *stream* son **NULL**, o si *path* es una cadena vacía, estas funciones invocan el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno en** **EINVAL** y devuelven **EINVAL**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen_s**|**freopen_s**|**freopen_s**|**_wfreopen_s**|

**freopen_s** se utiliza normalmente para redirigir los archivos preabiertos **stdin**, **stdout**y **stderr** a los archivos especificados por el usuario. El nuevo archivo asociado a *la secuencia* se abre con *mode*, que es una cadena de caracteres que especifica el tipo de acceso solicitado para el archivo, como se indica a continuación:

|*Modo*|Acceso|
|-|-|
| **"R"** | Abre para lectura. Si el archivo no existe o no se puede encontrar, se produce un error en la **llamada freopen_s.** |
| **"W"** | Abre un archivo vacío para escritura. Si el archivo especificado existe, se destruye su contenido. |
| **"A"** | Abre para escritura al final del archivo (anexo) sin eliminar el marcador de fin de archivo (EOF) antes de que se escriban nuevos datos en el archivo. Crea el archivo si no existe. |
| **"r+"** | Abre para lectura y escritura. El archivo debe existir. |
| **"w+"** | Abre un archivo vacío para lectura y escritura. Si el archivo existe, se destruye su contenido. |
| **"a+"** | Se abre para lectura y anexado. La operación de anexado incluye la eliminación del marcador EOF antes de que los nuevos datos se escriban en el archivo. El marcador EOF no se restablece una vez completada la escritura. Crea el archivo si no existe. |

Utilice los tipos **"w"** y **"w+"** con cuidado, ya que pueden destruir los archivos existentes.

Cuando se abre un archivo con el tipo de acceso **"a"** o **"a+",** todas las operaciones de escritura tienen lugar al final del archivo. Aunque el puntero de archivo se puede cambiar de posición mediante [fseek](fseek-fseeki64.md) o [rebobinado](rewind.md), el puntero de archivo siempre se mueve de nuevo al final del archivo antes de que se lleve a cabo cualquier operación de escritura. Por lo tanto, los datos existentes no se pueden sobrescribir.

El modo **"a"** no elimina el marcador EOF antes de anexar al archivo. Una vez realizado el anexado, el comando TYPE de MS-DOS solo muestra los datos hasta el marcador EOF original, y no los datos anexados al archivo. El modo **"a+"** elimina el marcador EOF antes de anexar al archivo. Después de anexar, el comando TYPE de MS-DOS muestra todos los datos del archivo. El modo **"a+"** es necesario para anexar a un archivo de secuencia que se termina con el marcador EOF CTRL+Z.

Cuando se especifica el tipo de acceso **"r+"**, **"w+"** o **"a+",** se permiten tanto la lectura como la escritura (se dice que el archivo está abierto para "actualización"). En cambio, si se cambia entre lectura y escritura, debe haber una operación intermedia [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md) o [rewind](rewind.md). La posición actual se puede especificar para la operación [fsetpos](fsetpos.md) o [fseek,](fseek-fseeki64.md) si lo desea. Además de los valores anteriores, se puede incluir uno de los siguientes caracteres en la cadena de *modo* para especificar el modo de traducción para las nuevas líneas.

|modificador *de modo*|Modo de traducción|
|-|-|
| **T** | Abra en modo de texto (traducido). |
| **B** | Abrir en modo binario (sin traducir); se suprimen las traducciones que implican caracteres de retorno de carro y de avance de línea. |

En el modo de texto (traducido), las combinaciones de avance de línea de retorno de carro (CR-LF) se traducen en caracteres de alimentación de línea única (LF) en la entrada; Los caracteres LF se traducen a combinaciones CR-LF en la salida. Además, CTRL+Z se interpreta como carácter de final de archivo en la entrada. En los archivos abiertos para leer o para escribir y leer con **"a+",** la biblioteca en tiempo de ejecución comprueba si hay CTRL+Z al final del archivo y la elimina, si es posible. Esto se hace porque el uso de [fseek](fseek-fseeki64.md) y [ftell](ftell-ftelli64.md) para moverse dentro de un archivo puede hacer que [fseek](fseek-fseeki64.md) se comporte incorrectamente cerca del final del archivo. La opción **t** es una extensión de Microsoft que no se debe utilizar cuando se desea la portabilidad ANSI.

Si **t** o **b** no se da en *modo*, el modo de traducción predeterminado se define mediante la variable global [_fmode](../../c-runtime-library/fmode.md). Si **t** o **b** tiene como prefijo el argumento, se produce un error en la función y devuelve **NULL**.

Para obtener una descripción de los modos de texto y binario, consulte [E/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**freopen_s**|\<stdio.h>|
|**_wfreopen_s**|\<stdio.h> o \<wchar.h>|

La consola no se admite en aplicaciones de la Plataforma universal de Windows (UWP). Los identificadores de secuencia estándar asociados a la consola, **stdin,** **stdout**y **stderr**, deben redirigirse antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones para UWP. Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_freopen_s.c
// This program reassigns stderr to the file
// named FREOPEN.OUT and writes a line to that file.

#include <stdio.h>
#include <stdlib.h>

FILE *stream;

int main( void )
{
   errno_t err;
   // Reassign "stderr" to "freopen.out":
   err = freopen_s( &stream, "freopen.out", "w", stderr );

   if( err != 0 )
      fprintf( stdout, "error on freopen\n" );
   else
   {
      fprintf( stdout, "successfully reassigned\n" ); fflush( stdout );
      fprintf( stream, "This will go to the file 'freopen.out'\n" );
      fclose( stream );
   }
   system( "type freopen.out" );
}
```

```Output
successfully reassigned
This will go to the file 'freopen.out'
```

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
