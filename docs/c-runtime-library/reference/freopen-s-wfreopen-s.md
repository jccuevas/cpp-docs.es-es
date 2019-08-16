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
ms.openlocfilehash: 6efe858713bf8c315536098f1b6dabdbcba01bfa
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376113"
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

*stream*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un código de error. Si se produce un error, el archivo original se cierra.

## <a name="remarks"></a>Comentarios

La función **freopen_s** cierra el archivo asociado actualmente a *Stream* y reasigna *Stream* al archivo especificado por *path*. **_wfreopen_s** es una versión con caracteres anchos de **_freopen_s**; los argumentos de *modo* y *ruta de acceso* a **_wfreopen_s** son cadenas de caracteres anchos. **_wfreopen_s** y **_freopen_s** se comportan de manera idéntica.

Si alguno de los valores de *pFile*, *path*, *mode*o *Stream* son **null**, o si *path* es una cadena vacía, estas funciones invocan el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** en **EINVAL** y devuelven **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen_s**|**freopen_s**|**freopen_s**|**_wfreopen_s**|

**freopen_s** se suele usar para redirigir los archivos previamente abiertos **stdin**, **stdout**y **stderr** a los archivos especificados por el usuario. El nuevo archivo asociado a *Stream* se abre con el *modo*, que es una cadena de caracteres que especifica el tipo de acceso solicitado para el archivo, como se indica a continuación:

|*mode*|Access|
|-|-|
| **"r"** | Abre para lectura. Si el archivo no existe o no se encuentra, se produce un error en la llamada a **freopen_s** . |
| **"w"** | Abre un archivo vacío para escritura. Si el archivo especificado existe, se destruye su contenido. |
| **"a"** | Abre para escritura al final del archivo (anexo) sin eliminar el marcador de fin de archivo (EOF) antes de que se escriban nuevos datos en el archivo. Crea el archivo si no existe. |
| **"r+"** | Abre para lectura y escritura. El archivo debe existir. |
| **"w+"** | Abre un archivo vacío para lectura y escritura. Si el archivo existe, se destruye su contenido. |
| **"a+"** | Se abre para lectura y anexado. La operación de anexado incluye la eliminación del marcador EOF antes de que los nuevos datos se escriban en el archivo. El marcador EOF no se restablece una vez completada la escritura. Crea el archivo si no existe. |

Use los tipos **"w"** y **"w +"** con cuidado, ya que pueden destruir archivos existentes.

Cuando un archivo se abre con el tipo de acceso **"a"** o **"a +"** , todas las operaciones de escritura tienen lugar al final del archivo. Aunque se puede cambiar la posición del puntero de archivo mediante [fseek](fseek-fseeki64.md) o rebobinar, el puntero de archivo siempre se desplaza al final del archivo antes de que se realice cualquier operación de escritura. [](rewind.md) Por consiguiente, los datos existentes no pueden sobrescribirse.

El modo **"a"** no quita el marcador EOF antes de anexar al archivo. Una vez realizado el anexado, el comando TYPE de MS-DOS solo muestra los datos hasta el marcador EOF original, y no los datos anexados al archivo. El modo **"a +"** quita el marcador EOF antes de anexar al archivo. Después de anexar, el comando TYPE de MS-DOS muestra todos los datos del archivo. El modo **"a +"** es necesario para anexar a un archivo de secuencia que termina con el marcador EOF Ctrl + Z.

Cuando se especifica el tipo de acceso **"r +"** , **"w +"** o **"a +"** , se permiten la lectura y la escritura (se dice que el archivo está abierto para "actualización"). En cambio, si se cambia entre lectura y escritura, debe haber una operación intermedia [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md) o [rewind](rewind.md). Si se desea, se puede especificar la posición actual para la operación [fsetpos](fsetpos.md) o [fseek](fseek-fseeki64.md) . Además de los valores anteriores, se puede incluir uno de los siguientes caracteres en la cadena de *modo* para especificar el modo de traducción para las nuevas líneas.

|modificador de *modo*|Modo de traducción|
|-|-|
| **t** | Abra en modo de texto (traducido). |
| **b** | Abrir en modo binario (sin traducir); se suprimen las traducciones que implican caracteres de retorno de carro y avance de línea. |

En el modo de texto (traducido), las combinaciones de retorno de carro y avance de línea (CR-LF) se traducen en caracteres de avance de línea (LF) en la entrada; Los caracteres de LF se traducen en combinaciones de CR-LF en la salida. Además, CTRL+Z se interpreta como carácter de final de archivo en la entrada. En los archivos abiertos para lectura o para escritura y lectura con **"a +"** , la biblioteca en tiempo de ejecución comprueba si hay un Ctrl + Z al final del archivo y lo quita, si es posible. Esto se hace porque el uso de [fseek](fseek-fseeki64.md) y [ftell](ftell-ftelli64.md) para desplace dentro de un archivo puede hacer que [fseek](fseek-fseeki64.md) se comporte de forma incorrecta cerca del final del archivo. La opción **t** es una extensión de Microsoft que no se debe usar si se desea disponer de portabilidad ANSI.

Si **t** o **b** no se especifican en el *modo*, el modo de traducción predeterminado se define mediante la variable global [_fmode](../../c-runtime-library/fmode.md). Si **t** o **b** tiene como prefijo el argumento, la función produce un error y devuelve **null**.

Para obtener una descripción de los modos de texto y binario, consulte [E/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**freopen_s**|\<stdio.h>|
|**_wfreopen_s**|\<stdio.h> o \<wchar.h>|

La consola no se admite en aplicaciones de Plataforma universal de Windows (UWP). Los identificadores de flujo estándar que están asociados a la consola, **stdin**, **stdout**y **stderr**deben redirigirse antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones para UWP. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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
