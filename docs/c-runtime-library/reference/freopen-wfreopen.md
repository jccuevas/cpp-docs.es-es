---
title: freopen, _wfreopen
ms.date: 11/04/2016
apiname:
- freopen
- _wfreopen
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
- _wfreopen
- _tfreopen
- freopen
helpviewer_keywords:
- _wfreopen function
- file pointers [C++], reassigning
- _tfreopen function
- freopen function
- tfreopen function
- wfreopen function
ms.assetid: de4b73f8-1043-4d62-98ee-30d2022da885
ms.openlocfilehash: 4fa5afb1baea33178c987b45e8b7dace4e4515eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649532"
---
# <a name="freopen-wfreopen"></a>freopen, _wfreopen

Reasigna un puntero de archivo. Hay disponibles versiones más seguras de estas funciones; consulte [freopen_s, _wfreopen_s](freopen-s-wfreopen-s.md).

## <a name="syntax"></a>Sintaxis

```C
FILE *freopen(
   const char *path,
   const char *mode,
   FILE *stream
);
FILE *_wfreopen(
   const wchar_t *path,
   const wchar_t *mode,
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*path*<br/>
Ruta de acceso del nuevo archivo.

*mode*<br/>
Tipo de acceso permitido.

*secuencia*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un puntero al archivo que se acaba de abrir. Si se produce un error, se cierra el archivo original y la función devuelve un **NULL** valor de puntero. Si *ruta*, *modo*, o *secuencia* es un puntero nulo, o si *filename* es una cadena vacía, estas funciones invocan el parámetro no válido controlador, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** a **EINVAL** y devolver **NULL**.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.

## <a name="remarks"></a>Comentarios

Existen versiones más seguras de estas funciones, consulte [freopen_s, _wfreopen_s](freopen-s-wfreopen-s.md).

El **freopen** función cierra el archivo asociado actualmente *secuencia* y reasigna *secuencia* en el archivo especificado por *ruta de acceso*. **_wfreopen** es una versión con caracteres anchos de **_freopen**; el *ruta* y *modo* argumentos **_wfreopen** son cadenas de caracteres anchos. **_wfreopen** y **_freopen** se comportan exactamente igual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen**|**freopen**|**freopen**|**_wfreopen**|

**freopen** normalmente se usa para redirigir los archivos ya abiertos **stdin**, **stdout**, y **stderr** a los archivos especificados por el usuario. El nuevo archivo asociado *secuencia* se abre con *modo*, que es una cadena de caracteres que especifica el tipo de acceso solicitado para el archivo, como se indica a continuación:

|*mode*|Access|
|-|-|
**"r"**|Abre para lectura. Si el archivo no existe o no se encuentra el **freopen** llamar se produce un error.
**"w"**|Abre un archivo vacío para escritura. Si el archivo especificado existe, se destruye su contenido.
**"a"**|Abre para escritura al final del archivo (anexo) sin eliminar el marcador de fin de archivo (EOF) antes de que se escriban nuevos datos en el archivo. Crea el archivo si no existe.
**"r+"**|Abre para lectura y escritura. El archivo debe existir.
**"w+"**|Abre un archivo vacío para lectura y escritura. Si el archivo existe, se destruye su contenido.
**"a+"**|Se abre para lectura y anexado. La operación de anexado incluye la eliminación del marcador EOF antes de que los nuevos datos se escriban en el archivo. El marcador EOF no se restablece una vez completada la escritura. Crea el archivo si no existe.

Use la **"w"** y **"w +"** tipos con cuidado, ya que podrían destruir archivos existentes.

Cuando se abre un archivo con el **"a"** o **"a +"** acceso tipo, todas las operaciones tienen lugar al final del archivo de escritura. Aunque se puede mover el puntero de archivo mediante [fseek](fseek-fseeki64.md) o [rebobinar](rewind.md), el puntero de archivo se desplaza siempre al final del archivo antes de cualquier escritura operación se lleva a cabo. Por consiguiente, los datos existentes no pueden sobrescribirse.

El **"a"** modo no quita el marcador EOF antes de anexar al archivo. Una vez realizado el anexado, el comando TYPE de MS-DOS solo muestra los datos hasta el marcador EOF original, y no los datos anexados al archivo. El **"a +"** modo quita el marcador EOF antes de anexar al archivo. Después de anexar, el comando TYPE de MS-DOS muestra todos los datos del archivo. El **"a +"** modo se requiere para anexar a un archivo de secuencia que se termina con el marcador EOF CTRL+Z.

Cuando el **"r +"**, **"w +"**, o **"a +"** se especifica el tipo de acceso, se permiten operaciones de lectura y escritura (se dice que el archivo esté abierto para "actualización"). En cambio, si se cambia entre lectura y escritura, debe haber una operación intermedia [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md) o [rewind](rewind.md). Se puede especificar la posición actual para el [fsetpos](fsetpos.md) o [fseek](fseek-fseeki64.md) operación, si lo desea. Además de los valores anteriores, uno de los siguientes caracteres puede incluirse en el *modo* cadena para especificar el modo de traducción de las líneas nuevas.

|*modo* modificador|Modo de traducción|
|-|-|
**t**|Abra en modo de texto (traducido).
**b**|Abra en modo binario (sin traducir); las traducciones que implican los caracteres de retorno de carro y avance de línea se suprimen.

En el modo de texto (traducido), combinaciones de retorno-salto de línea (CR-LF) de transporte se convierten en caracteres de avance de línea (LF) en la entrada; Los caracteres de LF se traducen a combinaciones CR-LF en la salida. Además, CTRL+Z se interpreta como carácter de final de archivo en la entrada. En los archivos abiertos para lectura o para escribir y leer con **"a +"**, la biblioteca en tiempo de ejecución comprueba un CTRL+Z al final del archivo y lo quita, si es posible. Esto se hace porque utilizar [fseek](fseek-fseeki64.md) y [ftell](ftell-ftelli64.md) para desplazarse por un archivo puede provocar [fseek](fseek-fseeki64.md) para que se comporte de forma incorrecta cerca del final del archivo. El **t** opción es una extensión de Microsoft que no debe usarse si desea usarse la portabilidad ANSI.

Si **t** o **b** no se proporciona en *modo*, el modo de traducción predeterminado está definido por la variable global [_fmode](../../c-runtime-library/fmode.md). Si **t** o **b** tiene como prefijo para el argumento, la función produce un error y devuelve **NULL**.

Para obtener una descripción de los modos de texto y binario, consulte [E/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**freopen**|\<stdio.h>|
|**_wfreopen**|\<stdio.h> o \<wchar.h>|

La consola no se admite en aplicaciones de la plataforma Universal de Windows (UWP). Los identificadores de secuencia estándar que están asociados con la consola, **stdin**, **stdout**, y **stderr**, se deben redirigir antes las funciones de tiempo de ejecución de C puedan usarlos en aplicaciones para UWP . Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_freopen.c
// compile with: /W3
// This program reassigns stderr to the file
// named FREOPEN.OUT and writes a line to that file.
#include <stdio.h>
#include <stdlib.h>

FILE *stream;

int main( void )
{
   // Reassign "stderr" to "freopen.out":
   stream = freopen( "freopen.out", "w", stderr ); // C4996
   // Note: freopen is deprecated; consider using freopen_s instead

   if( stream == NULL )
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

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
