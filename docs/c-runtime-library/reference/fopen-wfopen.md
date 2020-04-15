---
title: fopen, _wfopen
ms.date: 4/2/2020
api_name:
- _wfopen
- fopen
- _o__wfopen
- _o_fopen
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
- fopen
- _wfopen
- _tfopen
- corecrt_wstdio/_wfopen
- stdio/fopen
helpviewer_keywords:
- opening files, for file I/O
- wfopen function
- tfopen function
- _tfopen function
- _wfopen function
- files [C++], opening
- fopen function
ms.assetid: e868993f-738c-4920-b5e4-d8f2f41f933d
ms.openlocfilehash: 4b9fa6542996b2c16128a841e2611b85e995be2a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346405"
---
# <a name="fopen-_wfopen"></a>fopen, _wfopen

Abre un archivo. Hay disponibles versiones más seguras de estas funciones que realizan una validación de parámetros adicional y devuelven códigos de error; consulte [fopen_s, _wfopen_s](fopen-s-wfopen-s.md).

## <a name="syntax"></a>Sintaxis

```C
FILE *fopen(
   const char *filename,
   const char *mode
);
FILE *_wfopen(
   const wchar_t *filename,
   const wchar_t *mode
);
```

### <a name="parameters"></a>Parámetros

*Nombre*<br/>
Nombre de archivo.

*Modo*<br/>
Tipo de acceso habilitado.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un puntero al archivo abierto. Un valor de puntero null indica un error. Si *filename* o *mode* es **NULL** o una cadena vacía, estas funciones desencadenan el controlador de parámetros no válidos, que se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven **NULL** y **establecen errno en** **EINVAL**.

Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

La función **fopen** abre el archivo especificado por *filename*. De forma predeterminada, una cadena de nombre de *archivo* estrecho se interpreta mediante la página de códigos ANSI (CP_ACP). En las aplicaciones de escritorio de Windows, se puede cambiar a la página de códigos del OEM (CP_OEMCP) con la función [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) . Puede utilizar la función [AreFileApisANSI](/windows/win32/api/fileapi/nf-fileapi-arefileapisansi) para determinar si *el nombre* de archivo se interpreta mediante la ansi o la página de códigos OEM predeterminada del sistema. **_wfopen** es una versión de caracteres anchos de **fopen**; los argumentos para **_wfopen** son cadenas de caracteres anchos. De lo contrario, **_wfopen** y **fopen** se comportan de forma idéntica. El solo uso de **_wfopen** no afecta al juego de caracteres codificado que se utiliza en la secuencia de archivos.

**fopen** acepta rutas de acceso que son válidas en el sistema de archivos en el punto de ejecución; **fopen** acepta rutas de acceso UNC y rutas de acceso que implican unidades de red asignadas siempre que el sistema que ejecuta el código tenga acceso al recurso compartido o a la unidad asignada en el momento de la ejecución. Al construir rutas de acceso para **fopen**, asegúrese de que las unidades, las rutas de acceso o los recursos compartidos de red estarán disponibles en el entorno de ejecución. Puede usar barras diagonales (/) o barras diagonales inversas (\\) como separadores de directorio en una ruta de acceso.

Compruebe siempre el valor devuelto para ver si el puntero es NULL antes de realizar ninguna otra operación en el archivo. Si se produce un error, se establece la variable global **errno** y se puede utilizar para obtener información de error específica. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="unicode-support"></a>Compatibilidad con Unicode

**fopen** admite secuencias de archivos Unicode. Para abrir un archivo Unicode, pase una marca **ccs** que especifique la codificación deseada para **fopen,** como se indica a continuación.

> **FILE \*fp = fopen("newfile.txt", "rt+, ccs=**_encoding_**");**

Los valores permitidos de *codificación* son **UNICODE**, **UTF-8**y **UTF-16LE**.

Cuando se abre un archivo en modo Unicode, las funciones de entrada traducen los datos que se leen del archivo en datos UTF-16 almacenados como tipo **wchar_t**. Las funciones que escriben en un archivo abierto en modo Unicode esperan búferes que contengan datos UTF-16 almacenados como tipo **wchar_t**. Si el archivo está codificado como UTF-8, los datos UTF-16 se traducen a UTF-8 cuando se escriben, y el contenido codificado en UTF-8 del archivo se traduce a UTF-16 cuando se lee. Un intento de leer o escribir un número impar de bytes en modo Unicode provoca un error de [validación](../../c-runtime-library/parameter-validation.md) de parámetros. Para leer o escribir datos almacenados en el programa como UTF-8, use un modo de archivo binario o de texto en lugar de un modo Unicode. Cualquier traducción de codificación que sea necesaria es su responsabilidad.

Si el archivo ya existe y está abierto para lectura o para anexar, la marca de orden de bytes (BOM), si está presente en el archivo, determina la codificación. La codificación de LA lista de materiales tiene prioridad sobre la codificación especificada por el indicador **ccs.** La codificación **ccs** solo se utiliza cuando no hay ninguna lista de materiales o el archivo es un archivo nuevo.

> [!NOTE]
> La detección de LDM solo se aplica a los archivos que se abren en modo Unicode (es decir, pasando el indicador **ccs).**

En la tabla siguiente se resumen los modos que se utilizan para varios indicadores **ccs** dados a **fopen** y marcas de orden de bytes en el archivo.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Codificaciones utilizadas basadas en el indicador de ccs y BOM

|ccs bandera|Ninguna BOM (o archivo nuevo)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Los archivos abiertos para escribir en el modo Unicode tienen una BOM escriba automáticamente.

Si *el modo* es **"a, ccs, codificación**_encoding_**ccs"**, **fopen** primero intenta abrir el archivo mediante el uso de acceso de lectura y escritura. Si esto se realiza correctamente, la función lee la BOM para determinar la codificación del archivo; si da error, la función utiliza la codificación predeterminada del archivo. En cualquier caso, **fopen** volverá a abrir el archivo mediante el acceso de solo escritura. (Esto se aplica únicamente al modo **"a",** no al modo **"a+".)**

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen**|**fopen**|**fopen**|**_wfopen**|

El *modo* de cadena de caracteres especifica el tipo de acceso que se solicita para el archivo, como se indica a continuación.

|*Modo*|Acceso|
|-|-|
| **"R"** | Abre para lectura. Si el archivo no existe o no se puede encontrar, se produce un error en la llamada **fopen.** |
| **"W"** | Abre un archivo vacío para escritura. Si el archivo especificado existe, se destruye su contenido. |
| **"A"** | Abre para escritura al final del archivo (anexo) sin eliminar el marcador de fin de archivo (EOF) antes de que se escriban nuevos datos en el archivo. Crea el archivo si no existe. |
| **"r+"** | Abre para lectura y escritura. El archivo debe existir. |
| **"w+"** | Abre un archivo vacío para lectura y escritura. Si el archivo existe, se destruye su contenido. |
| **"a+"** | Se abre para lectura y anexado. La operación de anexado incluye la eliminación del marcador EOF antes de que los nuevos datos se escriban en el archivo. El marcador EOF no se restablece una vez completada la escritura. Crea el archivo si no existe. |

Cuando se abre un archivo mediante el tipo de acceso **"a"** o el tipo de acceso **"a+",** todas las operaciones de escritura se producen al final del archivo. El puntero de archivo se puede cambiar de posición mediante [fseek](fseek-fseeki64.md) o [rebobinado](rewind.md), pero siempre se mueve de nuevo al final del archivo antes de realizar cualquier operación de escritura. Por consiguiente, los datos existentes no pueden sobrescribirse.

El modo **"a"** no elimina el marcador EOF antes de anexar al archivo. Una vez realizado el anexado, el comando TYPE de MS-DOS solo muestra los datos hasta el marcador EOF original, y no los datos anexados al archivo. Antes de anexar al archivo, el modo **"a+"** elimina el marcador EOF. Después de anexar, el comando TYPE de MS-DOS muestra todos los datos del archivo. El modo **"a+"** es necesario para anexar a un archivo de secuencia que se termina con el marcador EOF CTRL+Z.

Cuando se especifica el tipo de acceso **"r+"**, **"w+"** o **"a+",** se habilitan tanto la lectura como la escritura (se dice que el archivo está abierto para "actualización"). Sin embargo, cuando cambie de lectura a la escritura, la operación de entrada debe encontrar un marcador EOF. Si no hay ningún EOF, debe utilizar una llamada intermedia a una función de posición del archivo. Las funciones de posicionamiento de archivos son **fsetpos**, [fseek](fseek-fseeki64.md)y [rebobinar](rewind.md). Al cambiar de escritura a lectura, debe utilizar una llamada que intervenga a **fflush** o a una función de posicionamiento de archivos.

Además de los valores anteriores, se pueden anexar los siguientes caracteres al *modo* para especificar el modo de traducción para los caracteres de nueva línea.

|modificador *de modo*|Modo de traducción|
|-|-|
| **T** | Abra en modo de texto (traducido). |
| **B** | Abrir en modo binario (sin traducir); se suprimen las traducciones que implican caracteres de retorno de carro y de avance de línea. |

En el modo de texto, CTRL+Z se interpreta como un carácter EOF en la entrada. En los archivos que se abren para lectura/escritura mediante **"a+",** **fopen** comprueba si hay CTRL+Z al final del archivo y lo elimina, si es posible. Esto se hace porque el uso de [fseek](fseek-fseeki64.md) y **ftell** para moverse dentro de un archivo que termina con CTRL+Z puede hacer que [fseek](fseek-fseeki64.md) se comporte incorrectamente cerca del final del archivo.

En el modo de texto, las combinaciones de avance de línea de retorno de carro se traducen en avances de línea únicos en la entrada, y los caracteres de avance de línea se traducen en combinaciones de avance de línea de retorno de carro en la salida. Cuando una función de E/S de flujo Unicode funciona en el modo de texto (valor predeterminado), se asume que el flujo de origen o de destino son una secuencia de caracteres multibyte. Por consiguiente, las funciones de entrada de secuencias Unicode convierten los caracteres multibyte en caracteres anchos (como si se realizara una llamada a la función **mbtowc**). Por la misma razón, las funciones de salida de secuencias Unicode convierten los caracteres anchos en caracteres multibyte (como si se realizara una llamada a la función **wctomb**).

Si **t** o **b** no se da en *modo*, el modo de traducción predeterminado se define mediante la variable global [_fmode](../../c-runtime-library/fmode.md). Si **t** o **b** tiene como prefijo el argumento, se produce un error en la función y devuelve **NULL**.

Para más información sobre cómo utilizar los modos binario y de texto en Unicode y la E/S de flujo multibyte, vea [Text and Binary Mode File I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) y [E/S de secuencias Unicode en los modos binario y de texto](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

Las siguientes opciones se pueden anexar al *modo* para especificar comportamientos adicionales.

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

Caracteres válidos para la cadena de *modo* que se utiliza en **fopen** y **_fdopen** corresponden a argumentos *oflag* que se usan en [_open](open-wopen.md) y [_sopen](sopen-wsopen.md), como se indica a continuación.

|Caracteres en cadena *de modo*|Valor *oflag* \_equivalente\_para open/sopen|
|-------------------------------|----------------------------------------------------|
|**Un**|**\_O\_WRONLY** &#124; ** \_O\_APPEND** (normalmente ** \_O\_WRONLY** &#124; ** \_O\_CREAT** &#124; ** \_O\_APPEND**)|
|**a+**|**\_O\_RDWR** &#124; ** \_\_O APPEND** (normalmente ** \_O\_RDWR** &#124; ** \_O\_APPEND** &#124; ** \_O CREAT\_** )|
|**R**|**\_O\_RDONLY**|
|**r+**|**\_O\_RDWR**|
|**W**|**\_O\_WRONLY** (normalmente ** \_O\_WRONLY** &#124; ** \_O CREAT\_** &#124; ** \_O\_TRUNC)**|
|**w+**|**\_O\_RDWR** (normalmente ** \_\_O RDWR** &#124; ** \_\_O CREAT** &#124; ** \_O\_TRUNC**)|
|**B**|**\_O\_BINARY**|
|**T**|**\_O\_TEXTO**|
|**C**|None|
|**N**|None|
|**S**|**\_O\_SEQUENTIAL**|
|**R**|**\_O\_RANDOM**|
|**T**|**\_O\_SHORTLIVED**|
|**D**|**\_O\_TEMPORAL**|
|**ccs-UNICODE**|**\_O\_WTEXT**|
|**ccs=UTF-8**|**\_O\_UTF8**|
|**ccs-UTF-16LE**|**\_O\_UTF16**|

Si está utilizando el modo **rb,** no tiene que migrar el código y si espera leer la mayor parte de un archivo grande o no le preocupa el rendimiento de la red, también puede considerar si desea utilizar archivos Win32 asignados a memoria como una opción.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fopen**|\<stdio.h>|
|**_wfopen**|\<stdio.h> o \<wchar.h>|

**_wfopen** es una extensión de Microsoft. Para obtener más información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

Las opciones de *modo* **c**, **n**, **t**, **S**, **R**, **T**y **D** son extensiones de Microsoft para **fopen** y **_fdopen** y no se deben utilizar cuando se desea la portabilidad ANSI.

## <a name="example-1"></a>Ejemplo 1

El siguiente programa abre dos archivos.  Utiliza **fclose** para cerrar el primer archivo y **_fcloseall** para cerrar todos los archivos restantes.

```C
// crt_fopen.c
// compile with: /W3
// This program opens two files. It uses
// fclose to close the first file and
// _fcloseall to close all remaining files.

#include <stdio.h>

FILE *stream, *stream2;

int main( void )
{
   int numclosed;

   // Open for read (will fail if file "crt_fopen.c" does not exist)
   if( (stream  = fopen( "crt_fopen.c", "r" )) == NULL ) // C4996
   // Note: fopen is deprecated; consider using fopen_s instead
      printf( "The file 'crt_fopen.c' was not opened\n" );
   else
      printf( "The file 'crt_fopen.c' was opened\n" );

   // Open for write
   if( (stream2 = fopen( "data2", "w+" )) == NULL ) // C4996
      printf( "The file 'data2' was not opened\n" );
   else
      printf( "The file 'data2' was opened\n" );

   // Close stream if it is not NULL
   if( stream)
   {
      if ( fclose( stream ) )
      {
         printf( "The file 'crt_fopen.c' was not closed\n" );
      }
   }

   // All other files are closed:
   numclosed = _fcloseall( );
   printf( "Number of files closed by _fcloseall: %u\n", numclosed );
}
```

```Output
The file 'crt_fopen.c' was opened
The file 'data2' was opened
Number of files closed by _fcloseall: 1
```

## <a name="example-2"></a>Ejemplo 2

El siguiente programa crea un archivo (o sobrescribe uno si existe), en el modo de texto con codificación Unicode.  A continuación, escribe dos cadenas en el archivo y cierra el archivo. El resultado es un archivo denominado _wfopen_test.xml, que contiene los datos de la sección de salida.

```C
// crt__wfopen.c
// compile with: /W3
// This program creates a file (or overwrites one if
// it exists), in text mode using Unicode encoding.
// It then writes two strings into the file
// and then closes the file.

#include <stdio.h>
#include <stddef.h>
#include <stdlib.h>
#include <wchar.h>

#define BUFFER_SIZE 50

int main(int argc, char** argv)
{
    wchar_t str[BUFFER_SIZE];
    size_t  strSize;
    FILE*   fileHandle;

    // Create an the xml file in text and Unicode encoding mode.
    if ((fileHandle = _wfopen( L"_wfopen_test.xml",L"wt+,ccs=UNICODE")) == NULL) // C4996
    // Note: _wfopen is deprecated; consider using _wfopen_s instead
    {
        wprintf(L"_wfopen failed!\n");
        return(0);
    }

    // Write a string into the file.
    wcscpy_s(str, sizeof(str)/sizeof(wchar_t), L"<xmlTag>\n");
    strSize = wcslen(str);
    if (fwrite(str, sizeof(wchar_t), strSize, fileHandle) != strSize)
    {
        wprintf(L"fwrite failed!\n");
    }

    // Write a string into the file.
    wcscpy_s(str, sizeof(str)/sizeof(wchar_t), L"</xmlTag>");
    strSize = wcslen(str);
    if (fwrite(str, sizeof(wchar_t), strSize, fileHandle) != strSize)
    {
        wprintf(L"fwrite failed!\n");
    }

    // Close the file.
    if (fclose(fileHandle))
    {
        wprintf(L"fclose failed!\n");
    }
    return 0;
}
```

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
