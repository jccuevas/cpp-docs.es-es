---
title: fopen, _wfopen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wfopen
- fopen
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
- fopen
- _wfopen
- _tfopen
- corecrt_wstdio/_wfopen
- stdio/fopen
dev_langs:
- C++
helpviewer_keywords:
- opening files, for file I/O
- wfopen function
- tfopen function
- _tfopen function
- _wfopen function
- files [C++], opening
- fopen function
ms.assetid: e868993f-738c-4920-b5e4-d8f2f41f933d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b606f168448f833a8e244ad35e52faf4f0afd75
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405411"
---
# <a name="fopen-wfopen"></a>fopen, _wfopen

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

*filename*<br/>
Nombre de archivo.

*mode*<br/>
Tipo de acceso habilitado.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un puntero al archivo abierto. Un valor de puntero null indica un error. Si *filename* o *modo* es **NULL** o una cadena vacía, estas funciones inician el controlador de parámetros no válidos, como se describe en [parámetro Validación](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven **NULL** y establecer **errno** a **EINVAL**.

Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **fopen** función abre el archivo especificado por *filename*. De forma predeterminada, estrechas *filename* cadena se interpreta usando la página de códigos ANSI (CP_ACP). En las aplicaciones de escritorio de Windows, se puede cambiar a la página de códigos del OEM (CP_OEMCP) con la función [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534\(v=vs.85\).aspx) . Puede usar el [AreFileApisANSI](https://msdn.microsoft.com/library/windows/desktop/aa363781\(v=vs.85\).aspx) función para determinar si *filename* se interpreta usando el ANSI o la página de códigos OEM de sistema predeterminada. **_wfopen** es una versión con caracteres anchos de **fopen**; los argumentos a **_wfopen** son cadenas de caracteres anchos. En caso contrario, **_wfopen** y **fopen** se comportan exactamente igual. Si solo se usa **_wfopen** no afecta al juego de caracteres codificado que se utiliza en la secuencia de archivos.

**fopen** acepta las rutas válidas en el sistema de archivos en el momento de ejecución; **fopen** acepta las rutas UNC y las rutas que requieren unidades de red asignan siempre y cuando el sistema que ejecuta el código tenga acceso al recurso compartido o unidad asignan en tiempo de ejecución. Al construir rutas para **fopen**, asegúrese de que las unidades, rutas de acceso o recursos compartidos de red estará disponibles en el entorno de ejecución. Puede usar barras diagonales (/) o barras diagonales inversas (\\) como separadores de directorio en una ruta de acceso.

Compruebe siempre el valor devuelto para ver si el puntero es NULL antes de realizar ninguna otra operación en el archivo. Si se produce un error, la variable global **errno** se establece y puede utilizarse para obtener información específica del error. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="unicode-support"></a>Compatibilidad con Unicode

**fopen** admite secuencias de archivo Unicode. Para abrir un archivo Unicode, pase un **ccs** marca que especifica la codificación deseada a **fopen**, como se indica a continuación.

> **ARCHIVO *fp = fopen ("newfile.txt", "rt + ccs =**_codificación_**");**

Valores permitidos de *codificación* son **UNICODE**, **UTF-8**, y **UTF-16LE**.

Cuando se abre un archivo en modo Unicode, las funciones de entrada traducen los datos leídos desde el archivo a datos UTF-16 almacenados como de tipo **wchar_t**. Las funciones que escriben en un archivo abierto en modo Unicode esperan que haya búferes que contengan datos UTF-16 almacenados como de tipo **wchar_t**. Si el archivo está codificado como UTF-8, los datos UTF-16 se traducen a UTF-8 cuando se escriben, y el contenido codificado en UTF-8 del archivo se traduce a UTF-16 cuando se lee. Si se trata de leer o escribir un número impar de bytes en el modo Unicode, se producirá un error de [validación de parámetros](../../c-runtime-library/parameter-validation.md) . Para leer o escribir datos almacenados en el programa como UTF-8, use un modo de archivo binario o de texto en lugar de un modo Unicode. Cualquier traducción de codificación que sea necesaria es su responsabilidad.

Si el archivo ya existe y está abierto para lectura o para anexar, la marca de orden de bytes (BOM), si está presente en el archivo, determina la codificación. La codificación de BOM tiene prioridad sobre la codificación especificada por el **ccs** marca. El **ccs** codificación sólo se utiliza cuando no hay BOM presente o el archivo es un archivo nuevo.

> [!NOTE]
> Detección de BOM solo se aplica a los archivos que se abren en el modo Unicode (es decir, pasando el **ccs** marca).

En la tabla siguiente resume los modos que se usan para distintos **ccs** marcas dados a **fopen** y las marcas de orden de bytes en el archivo.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Codificaciones utilizadas basadas en el indicador de ccs y BOM

|el indicador de CCS|Ninguna BOM (o archivo nuevo)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Los archivos abiertos para escribir en el modo Unicode tienen una BOM escriba automáticamente.

Si *modo* es **", ccs =**_codificación_**"**, **fopen** intenta primero abrir el archivo mediante el uso de lectura y acceso de escritura. Si esto se realiza correctamente, la función lee la BOM para determinar la codificación del archivo; si da error, la función utiliza la codificación predeterminada del archivo. En cualquier caso, **fopen** , a continuación, vuelva a abrir el archivo mediante el acceso de solo escritura. (Esto se aplica a **"a"** modo solo, no al **"+"** modo.)

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen**|**fopen**|**fopen**|**_wfopen**|

La cadena de caracteres *modo* especifica el tipo de acceso solicitado para el archivo, como se indica a continuación.

|*mode*|Access|
|-|-|
**"r"**|Abre para lectura. Si el archivo no existe o no se encuentra, el **fopen** llamadas se produce un error.
**"w"**|Abre un archivo vacío para escritura. Si el archivo especificado existe, se destruye su contenido.
**"a"**|Abre para escritura al final del archivo (anexo) sin eliminar el marcador de fin de archivo (EOF) antes de que se escriban nuevos datos en el archivo. Crea el archivo si no existe.
**"r+"**|Abre para lectura y escritura. El archivo debe existir.
**"w+"**|Abre un archivo vacío para lectura y escritura. Si el archivo existe, se destruye su contenido.
**"a+"**|Se abre para lectura y anexado. La operación de anexado incluye la eliminación del marcador EOF antes de que los nuevos datos se escriban en el archivo. El marcador EOF no se restablece una vez completada la escritura. Crea el archivo si no existe.

Cuando se abre un archivo mediante la **"a"** tipo de acceso o la **"+"** tipo, de acceso todas las operaciones de escritura aparecen al final del archivo. Se puede mover el puntero de archivo mediante el uso de [fseek](fseek-fseeki64.md) o [rebobinar](rewind.md), pero se desplaza siempre al final del archivo antes de cualquier escritura que se realiza la operación. Por consiguiente, los datos existentes no pueden sobrescribirse.

El **"a"** modo no quita el marcador EOF antes de que se anexe al archivo. Una vez realizado el anexado, el comando TYPE de MS-DOS solo muestra los datos hasta el marcador EOF original, y no los datos anexados al archivo. Antes de que se anexe al archivo, el **"+"** modo quita el marcador EOF. Después de anexar, el comando TYPE de MS-DOS muestra todos los datos del archivo. El **"+"** modo se requiere para anexar a un archivo de streaming terminado con el marcador EOF CTRL+Z.

Cuando el **"r +"**, **"w +"**, o **"+"** se especifica el tipo de acceso, se habilitan la lectura y escritura (se dice que el archivo esté abierto para "actualización"). Sin embargo, cuando cambie de lectura a la escritura, la operación de entrada debe encontrar un marcador EOF. Si no hay ningún EOF, debe utilizar una llamada intermedia a una función de posición del archivo. Las funciones de posición de archivo son **fsetpos**, [fseek](fseek-fseeki64.md), y [rebobinar](rewind.md). Cuando cambie de escritura a lectura, debe utilizar una llamada intermedia a **fflush** o a un archivo en función de posicionamiento.

Además de los valores anteriores, los caracteres siguientes se pueden anexar a *modo* para especificar el modo de traducción de caracteres de nueva línea.

|*modo* modificador|Modo de traducción|
|-|-|
**t**|Abra en modo de texto (traducido).
**b**|Abra en modo binario (sin traducir); las traducciones que implican los caracteres de retorno de carro y avance de línea se suprimen.

En modo de texto, CTRL+Z se interpreta como un carácter EOF en entrada. En archivos abiertos para lectura/escritura mediante el uso de **"+"**, **fopen** comprueba si hay un CTRL+Z al final del archivo y lo quita, si es posible. Esto se hace porque utilizar [fseek](fseek-fseeki64.md) y **ftell** para desplazarse por un archivo que finaliza con CTRL+Z puede hacer [fseek](fseek-fseeki64.md) se comporten de forma incorrecta cerca del final del archivo.

En modo de texto, combinaciones de avance de línea de retorno de carro se traducen en avances de línea únicos en la entrada y caracteres de avance de línea se traducen en combinaciones de avance de línea de retorno de carro en la salida. Cuando una función de E/S de flujo Unicode funciona en el modo de texto (valor predeterminado), se asume que el flujo de origen o de destino son una secuencia de caracteres multibyte. Por lo tanto, las funciones de entrada y flujo Unicode convierten los caracteres multibyte en caracteres anchos (como si se realizara una llamada a la **mbtowc** función). Por la misma razón, las funciones de salida y flujo Unicode convierten los caracteres anchos a caracteres multibyte (como si se realizara una llamada a la **wctomb** función).

Si **t** o **b** no se proporciona en *modo*, el modo de traducción predeterminado está definido por la variable global [_fmode](../../c-runtime-library/fmode.md). Si **t** o **b** tiene como prefijo al argumento, la función se produce un error y devuelve **NULL**.

Para más información sobre cómo utilizar los modos binario y de texto en Unicode y la E/S de flujo multibyte, vea [Text and Binary Mode File I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) y [Unicode Stream I/O in Text and Binary Modes](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

Las siguientes opciones se pueden anexar a *modo* para especificar comportamientos adicionales.

|*modo* modificador|Comportamiento|
|-|-|
**c**|Habilite la marca de confirmación para la asociada *filename* para que el contenido del búfer del archivo se escriba directamente en disco si **fflush** o **_flushall** se llama.
**n**|Restaure la marca de confirmación para la asociada *filename* a "no-commit". Este es el valor predeterminado. También invalida la marca global de confirmación si vincula el programa a COMMODE.OBJ. El valor predeterminado de la marca de confirmación global es "no-commit", a menos que vincule explícitamente el programa a COMMODE.OBJ (vea [Link Options](../../c-runtime-library/link-options.md)).
**N**|Especifica que el archivo no se hereda mediante procesos secundarios.
**S**|Especifica que el almacenamiento en caché está optimizado para el acceso secuencial (pero no restringido a este) desde el disco.
**R**|Especifica que el almacenamiento en caché está optimizado para el acceso aleatorio (pero no restringido a este) desde el disco.
**T**|Especifica un archivo como temporal. Si es posible, no se vuelca en el disco.
**D**|Especifica un archivo como temporal. Se elimina cuando se cierra el puntero del último archivo.
**CCS =**_codificación_|Especifica el carácter codificado establecido (uno de **UTF-8**, **UTF-16LE**, o **UNICODE**) para este archivo. Deje sin especificar si desea la codificación ANSI.

Los caracteres válidos para el *modo* cadena que se utiliza en **fopen** y **_fdopen** corresponden a *oflag* argumentos que se usan en [_open](open-wopen.md) y [_sopen](sopen-wsopen.md), como se indica a continuación.

|Caracteres de *modo* cadena|Equivalente *oflag* valor para _open/_sopen|
|-------------------------------|----------------------------------------------------|
|**a**|**_O_WRONLY** &#124; **_O_APPEND** (normalmente **_O_WRONLY** &#124; **_O_CREAT** &#124;** _O_APPEND **)|
|**a +**|**_O_RDWR** &#124; **_O_APPEND** (normalmente **_O_RDWR** &#124; **_O_APPEND** &#124; **_O_CREAT** )|
|**r**|**_O_RDONLY**|
|**r +**|**_O_RDWR**|
|**W**|**_O_WRONLY** (normalmente **_O_WRONLY** &#124; **_O_CREAT** &#124;** _O_TRUNC **)|
|**w +**|**_O_RDWR** (normalmente **_O_RDWR** &#124; **_O_CREAT** &#124; **_O_TRUNC**)|
|**b**|**_O_BINARY**|
|**t**|**_O_TEXT**|
|**c**|Ninguna|
|**n**|Ninguna|
|**S**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**CCS = UNICODE**|**_O_WTEXT**|
|**CCS = UTF-8**|**_O_UTF8**|
|**CCS = UTF-16LE**|**_O_UTF16**|

Si utilizas **rb** modo, no es necesario migrar el código, y si se va a leer la mayor parte de un archivo grande o no se preocupa el rendimiento de red, también puede considerar si usar memoria asignados archivos de Win32 como una opción.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fopen**|\<stdio.h>|
|**_wfopen**|\<stdio.h> o \<wchar.h>|

**_wfopen** es una extensión de Microsoft. Para obtener más información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

El **c**, **n**, **t**, **S**, **R**, **T**, y **d.**  *modo* opciones son extensiones de Microsoft para **fopen** y **_fdopen** y no debe usarse si desea usarse la portabilidad ANSI.

## <a name="example-1"></a>Ejemplo 1

El siguiente programa abre dos archivos.  Usa **fclose** para cerrar el primer archivo y **_fcloseall** para cerrar todos los archivos restantes.

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

## <a name="see-also"></a>Vea también

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
