---
title: fopen_s, _wfopen_s
ms.date: 4/2/2020
api_name:
- _wfopen_s
- fopen_s
- _o__wfopen_s
- _o_fopen_s
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
- fopen_s
- _tfopen_s
- _wfopen_s
helpviewer_keywords:
- _wfopen_s function
- opening files, for file I/O
- _tfopen_s function
- tfopen_s function
- wfopen_s function
- fopen_s function
- Unicode [C++], creating files
- Unicode [C++], writing files
- files [C++], opening
- Unicode [C++], files
ms.assetid: c534857e-39ee-4a3f-bd26-dfe551ac96c3
ms.openlocfilehash: 80d04e75637cfab9795bf5dfb9da9786cf4ebd71
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346488"
---
# <a name="fopen_s-_wfopen_s"></a>fopen_s, _wfopen_s

Abre un archivo. Estas versiones de [fopen, _wfopen](fopen-wfopen.md) incluyen mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t fopen_s(
   FILE** pFile,
   const char *filename,
   const char *mode
);
errno_t _wfopen_s(
   FILE** pFile,
   const wchar_t *filename,
   const wchar_t *mode
);
```

### <a name="parameters"></a>Parámetros

*pFile*<br/>
Puntero al puntero de archivo que recibirá el puntero al archivo abierto.

*Nombre*<br/>
Nombre de archivo.

*Modo*<br/>
Tipo de acceso permitido.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error. Consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos códigos de error.

### <a name="error-conditions"></a>Condiciones de error

|*pFile*|*Nombre*|*Modo*|Valor devuelto|Contenido de *pFile*|
|-------------|----------------|------------|------------------|------------------------|
|**Null**|cualquiera|cualquiera|**EINVAL**|sin cambios|
|cualquiera|**Null**|cualquiera|**EINVAL**|sin cambios|
|cualquiera|cualquiera|**Null**|**EINVAL**|sin cambios|

## <a name="remarks"></a>Observaciones

Los archivos abiertos por **fopen_s** y **_wfopen_s** no se pueden combinar. Si necesita que un archivo se pueda compartir, utilice [_fsopen, _wfsopen](fsopen-wfsopen.md) con la constante de modo de uso compartido adecuada, por ejemplo, **_SH_DENYNO** para compartir lectura y escritura.

La función **fopen_s** abre el archivo especificado por *filename*. **_wfopen_s** es una versión de caracteres anchos de **fopen_s;** los argumentos para **_wfopen_s** son cadenas de caracteres anchos. **_wfopen_s** y **fopen_s** comportarse de forma idéntica de lo contrario.

**fopen_s** acepta rutas de acceso que son válidas en el sistema de archivos en el punto de ejecución; Las rutas de acceso UNC y las rutas de acceso que implican unidades de red asignadas son aceptadas por **fopen_s** siempre que el sistema que ejecuta el código tenga acceso al recurso compartido o a la unidad de red asignada en el momento de la ejecución. Al crear rutas de acceso para **fopen_s**, no haga suposiciones sobre la disponibilidad de unidades, rutas de acceso o recursos compartidos de red en el entorno de ejecución. Puede usar barras diagonales (/) o barras diagonales inversas (\\) como separadores de directorio en una ruta de acceso.

Estas funciones validan sus parámetros. Si *pFile*, *filename*o *mode* es un puntero nulo, estas funciones generan una excepción de parámetro no válida, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).

Compruebe siempre el valor devuelto para ver si la función se realizó correctamente antes de realizar cualquier otra operación en el archivo. Si se produce un error, se devuelve el código de error y se establece la variable global **errno.** Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="unicode-support"></a>Compatibilidad con Unicode

**fopen_s** admite secuencias de archivos Unicode. Para abrir un archivo Unicode nuevo o existente, pase una marca *ccs* que especifique la codificación deseada para **fopen_s:**

**fopen_s(&fp, "newfile.txt", "rw, ccs=**_encoding_**");**

Los valores permitidos de *codificación* son **UNICODE**, **UTF-8**y **UTF-16LE**. Si no se especifica ningún valor para la *codificación,* **fopen_s** utiliza la codificación ANSI.

Si el archivo ya existe y está abierto para lectura o para anexar, la marca de orden de bytes (BOM), si está presente en el archivo, determina la codificación. La codificación de LDM tiene prioridad sobre la codificación especificada por el indicador *ccs.* La codificación *ccs* solo se utiliza cuando no hay ninguna lista de materiales o si el archivo es un archivo nuevo.

> [!NOTE]
> La detección de LDM solo se aplica a los archivos que se abren en modo Unicode; es decir, pasando la bandera *ccs.*

En la tabla siguiente se resumen los modos para varios indicadores *ccs* que se dan a **fopen_s** y para las marcas de orden de bytes en el archivo.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Codificaciones utilizadas basadas en el indicador de ccs y BOM

|ccs bandera|Ninguna BOM (o archivo nuevo)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

En los archivos que se abren para escribir en el modo Unicode se escribe una BOM automáticamente.

Si *el modo* es **"a, ccs,**_codificación_**ccs"**, **fopen_s** primero intenta abrir el archivo con acceso de lectura y escritura. Si la operación se realiza correctamente, la función lee la BOM para determinar la codificación del archivo; si se produce un error, la función usa la codificación predeterminada del archivo. En cualquier caso, **fopen_s** volver a abrir el archivo con acceso de solo escritura. (Esto se aplica a **un** modo solamente, no **a +**.)

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen_s**|**fopen_s**|**fopen_s**|**_wfopen_s**|

El *modo* de cadena de caracteres especifica el tipo de acceso que se solicita para el archivo, como se indica a continuación.

|*Modo*|Acceso|
|-|-|
| **"R"** | Abre para lectura. Si el archivo no existe o no se puede encontrar, se produce un error en la llamada **fopen_s.** |
| **"W"** | Abre un archivo vacío para escritura. Si el archivo especificado existe, se destruye su contenido. |
| **"A"** | Abre para escritura al final del archivo (anexo) sin eliminar el marcador de fin de archivo (EOF) antes de que se escriban nuevos datos en el archivo. Crea el archivo si no existe. |
| **"r+"** | Abre para lectura y escritura. El archivo debe existir. |
| **"w+"** | Abre un archivo vacío para lectura y escritura. Si el archivo existe, se destruye su contenido. |
| **"a+"** | Se abre para lectura y anexado. La operación de anexado incluye la eliminación del marcador EOF antes de que los nuevos datos se escriban en el archivo. El marcador EOF no se restablece una vez completada la escritura. Crea el archivo si no existe. |

Cuando se abre un archivo mediante el tipo de acceso **"a"** o **"a+",** todas las operaciones de escritura se producen al final del archivo. El puntero de archivo se puede cambiar de posición mediante [fseek](fseek-fseeki64.md) o [rebobinado](rewind.md), pero siempre se mueve de nuevo al final del archivo antes de que se lleve a cabo cualquier operación de escritura para que los datos existentes no se puedan sobrescribir.

El modo **"a"** no elimina el marcador EOF antes de anexar al archivo. Una vez realizado el anexado, el comando TYPE de MS-DOS solo muestra los datos hasta el marcador EOF original, y no los datos anexados al archivo. El modo **"a+"** elimina el marcador EOF antes de anexar al archivo. Después de anexar, el comando TYPE de MS-DOS muestra todos los datos del archivo. El modo **"a+"** es necesario para anexar a un archivo de secuencia que se termina mediante el marcador EOF CTRL+Z.

Cuando se especifica el tipo de acceso **"r+"**, **"w+"** o **"a+",** se permiten tanto la lectura como la escritura. (Se dice que el archivo está abierto para "actualizar".) Sin embargo, al cambiar de lectura a escritura, la operación de entrada debe encontrar un marcador EOF. Si no hay ningún EOF, debe usar una llamada intermedia a una función de posición del archivo. Las funciones de posicionamiento de archivos son **fsetpos**, [fseek](fseek-fseeki64.md)y [rebobinado](rewind.md). Al cambiar de escritura a lectura, debe utilizar una llamada que intervenga a **fflush** o a una función de posicionamiento de archivos.

Además de los valores anteriores, se pueden incluir los siguientes caracteres en el *modo* para especificar el modo de traducción para los caracteres de nueva línea:

|modificador *de modo*|Modo de traducción|
|-|-|
| **T** | Abra en modo de texto (traducido). |
| **B** | Abrir en modo binario (sin traducir); se suprimen las traducciones que implican caracteres de retorno de carro y de avance de línea. |

En el modo de texto (traducido), CTRL+Z se interpreta como un carácter de fin de archivo en la entrada. En los archivos abiertos para leer/escribir con **"a+"**, **fopen_s** comprueba si hay CTRL+Z al final del archivo y lo elimina, si es posible. Esto se hace porque el uso de [fseek](fseek-fseeki64.md) y **ftell** para moverse dentro de un archivo que termina con CTRL+Z, puede hacer que [fseek](fseek-fseeki64.md) se comporte incorrectamente cerca del final del archivo.

Además, en el modo de texto, las combinaciones de avance de línea de retorno de carro se traducen en fuentes de una sola línea en la entrada, y los caracteres de avance de línea se traducen en combinaciones de avance de línea de retorno de carro en la salida. Cuando una función de E/S de flujo Unicode funciona en el modo de texto (valor predeterminado), se asume que el flujo de origen o de destino son una secuencia de caracteres multibyte. Por consiguiente, las funciones de entrada de secuencias Unicode convierten los caracteres multibyte en caracteres anchos (como si se realizara una llamada a la función **mbtowc**). Por la misma razón, las funciones de salida de secuencias Unicode convierten los caracteres anchos en caracteres multibyte (como si se realizara una llamada a la función **wctomb**).

Si **t** o **b** no se da en *modo*, el modo de traducción predeterminado se define mediante la variable global [_fmode](../../c-runtime-library/fmode.md). Si **t** o **b** tiene como prefijo el argumento, se produce un error en la función y devuelve **NULL**.

Para obtener más información sobre el uso de los modos de texto y binario en E/S de secuencias Unicode y multibyte, consulte [E/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md) y [E/S de secuencias Unicode en los modos binario y de texto](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

|modificador *de modo*|Comportamiento|
|-|-|
| **C** | Habilite el indicador de confirmación para el nombre de *archivo* asociado para que el contenido del búfer de archivos se escriba directamente en el disco si se llama a **fflush** o **_flushall.** |
| **N** | Restablezca la marca de confirmación para el nombre de *archivo* asociado a "no-commit." Este es el valor predeterminado. También invalida la marca global de confirmación si vincula el programa a COMMODE.OBJ. El valor predeterminado de la marca de confirmación global es "no-commit", a menos que vincule explícitamente el programa a COMMODE.OBJ (vea [Opciones de vínculo](../../c-runtime-library/link-options.md)). |
| **N** | Especifica que el archivo no se hereda mediante procesos secundarios. |
| **S** | Especifica que el almacenamiento en caché está optimizado para el acceso secuencial (pero no restringido a este) desde el disco. |
| **R** | Especifica que el almacenamiento en caché está optimizado para el acceso aleatorio (pero no restringido a este) desde el disco. |
| **T** | Especifica un archivo como temporal. Si es posible, no se vuelca en el disco. |
| **D** | Especifica un archivo como temporal. Se elimina cuando se cierra el puntero del último archivo. |
| **ccs=**_encoding_ | Especifica el juego de caracteres codificado que se va a utilizar (uno de **UTF-8,** **UTF-16LE**o **UNICODE)** para este archivo. Deje sin especificar si desea la codificación ANSI. |

Los caracteres válidos para la cadena de *modo* utilizada en **fopen_s** y [_fdopen](fdopen-wfdopen.md) corresponden a argumentos *oflag* utilizados en [_open](open-wopen.md) y [_sopen](sopen-wsopen.md), como se indica a continuación.

|Caracteres en cadena *de modo*|Valor *oflag* equivalente para _open/_sopen|
|-------------------------------|----------------------------------------------------|
|**Un**|**_O_WRONLY** **_O_APPEND** &#124; (normalmente &#124; **_O_WRONLY** _O_CREAT **_O_CREAT** &#124;** _O_APPEND**)|
|**a+**|**_O_RDWR** &#124; **_O_APPEND** (usually **_O_RDWR** &#124; **_O_APPEND** &#124; **_O_CREAT** )|
|**R**|**_O_RDONLY**|
|**r+**|**_O_RDWR**|
|**W**|**_O_WRONLY** (usually **_O_WRONLY** &#124; **_O_CREAT** &#124;** _O_TRUNC**)|
|**w+**|**_O_RDWR** (usually **_O_RDWR** &#124; **_O_CREAT** &#124; **_O_TRUNC**)|
|**B**|**_O_BINARY**|
|**T**|**_O_TEXT**|
|**C**|None|
|**N**|None|
|**S**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**ccs-UNICODE**|**_O_WTEXT**|
|**ccs=UTF-8**|**_O_UTF8**|
|**ccs-UTF-16LE**|**_O_UTF16**|

Si está utilizando el modo **rb,** no necesitará portar el código y espera leer mucho del archivo y/o no le importa el rendimiento de la red, los archivos Win32 asignados a memoria también pueden ser una opción.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fopen_s**|\<stdio.h>|
|**_wfopen_s**|\<stdio.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

Las opciones de **t** *modo* **c**, **n**y t son extensiones de Microsoft para **fopen_s** y [_fdopen](fdopen-wfdopen.md) y no se deben utilizar cuando se desea la portabilidad ANSI.

## <a name="example"></a>Ejemplo

```C
// crt_fopen_s.c
// This program opens two files. It uses
// fclose to close the first file and
// _fcloseall to close all remaining files.

#include <stdio.h>

FILE *stream, *stream2;

int main( void )
{
   errno_t err;

   // Open for read (will fail if file "crt_fopen_s.c" does not exist)
   err  = fopen_s( &stream, "crt_fopen_s.c", "r" );
   if( err == 0 )
   {
      printf( "The file 'crt_fopen_s.c' was opened\n" );
   }
   else
   {
      printf( "The file 'crt_fopen_s.c' was not opened\n" );
   }

   // Open for write
   err = fopen_s( &stream2, "data2", "w+" );
   if( err == 0 )
   {
      printf( "The file 'data2' was opened\n" );
   }
   else
   {
      printf( "The file 'data2' was not opened\n" );
   }

   // Close stream if it is not NULL
   if( stream )
   {
      err = fclose( stream );
      if ( err == 0 )
      {
         printf( "The file 'crt_fopen_s.c' was closed\n" );
      }
      else
      {
         printf( "The file 'crt_fopen_s.c' was not closed\n" );
      }
   }

   // All other files are closed:
   int numclosed = _fcloseall( );
   printf( "Number of files closed by _fcloseall: %u\n", numclosed );
}
```

```Output
The file 'crt_fopen_s.c' was opened
The file 'data2' was opened
Number of files closed by _fcloseall: 1
```

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
