---
title: freopen_s, _wfreopen_s
ms.date: 11/04/2016
apiname:
- _wfreopen_s
- freopen_s
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
ms.openlocfilehash: 44e1cb14032d004e63825bf7b551d5f43ae400d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567601"
---
# <a name="freopens-wfreopens"></a>freopen_s, _wfreopen_s

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

*mode*<br/>
Tipo de acceso permitido.

*secuencia*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un código de error. Si se produce un error, el archivo original se cierra.

## <a name="remarks"></a>Comentarios

El **freopen_s** función cierra el archivo asociado actualmente *secuencia* y reasigna *secuencia* en el archivo especificado por *ruta de acceso* . **_wfreopen_s** es una versión con caracteres anchos de **_freopen_s**; el *ruta* y *modo* argumentos **_wfreopen_s** son cadenas de caracteres anchos. **_wfreopen_s** y **_freopen_s** se comportan exactamente igual.

Si cualquiera de *pFile*, *ruta*, *modo*, o *secuencia* son **NULL**, o si *derutadeacceso* es una cadena vacía, estas funciones invocan el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** a **EINVAL** y devolver **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen_s**|**freopen_s**|**freopen_s**|**_wfreopen_s**|

**freopen_s** normalmente se usa para redirigir los archivos ya abiertos **stdin**, **stdout**, y **stderr** a los archivos especificados por el usuario. El nuevo archivo asociado *secuencia* se abre con *modo*, que es una cadena de caracteres que especifica el tipo de acceso solicitado para el archivo, como se indica a continuación:

|*mode*|Access|
|-|-|
**"r"**|Abre para lectura. Si el archivo no existe o no se encuentra el **freopen_s** llamar se produce un error.
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
|**freopen_s**|\<stdio.h>|
|**_wfreopen_s**|\<stdio.h> o \<wchar.h>|

La consola no se admite en aplicaciones de la plataforma Universal de Windows (UWP). Los identificadores de secuencia estándar que están asociados con la consola, **stdin**, **stdout**, y **stderr**, se deben redirigir antes las funciones de tiempo de ejecución de C puedan usarlos en aplicaciones para UWP . Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
