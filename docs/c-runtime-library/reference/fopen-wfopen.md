---
title: fopen, _wfopen
ms.date: 11/04/2016
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
helpviewer_keywords:
- opening files, for file I/O
- wfopen function
- tfopen function
- _tfopen function
- _wfopen function
- files [C++], opening
- fopen function
ms.assetid: e868993f-738c-4920-b5e4-d8f2f41f933d
ms.openlocfilehash: b57ed2b26428c48efbe544c2b4802e347b915c29
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499939"
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

*filename*<br/>
Nombre de archivo.

*mode*<br/>
Tipo de acceso habilitado.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un puntero al archivo abierto. Un valor de puntero null indica un error. Si *filename* o *mode* es **null** o una cadena vacía, estas funciones desencadenan el controlador de parámetros no válidos, que se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven **null** y establecen **errno** en **EINVAL**.

Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

La función **fopen** abre el archivo especificado por *filename*. De forma predeterminada, una cadena de *nombre de archivo* estrecha se interpreta mediante la página de códigos ANSI (CP_ACP). En las aplicaciones de escritorio de Windows, se puede cambiar a la página de códigos del OEM (CP_OEMCP) con la función [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) . Puede usar la función [AreFileApisANSI](/windows/win32/api/fileapi/nf-fileapi-arefileapisansi) para determinar si *filename* se interpreta mediante ANSI o la página de códigos OEM predeterminada del sistema. **_wfopen** es una versión con caracteres anchos de **fopen**; los argumentos de **_wfopen** son cadenas de caracteres anchos. De lo contrario, **_wfopen** y **fopen** se comportan exactamente igual. Simplemente el uso de **_wfopen** no afecta al Juego de caracteres codificado que se usa en la secuencia de archivos.

**fopen** acepta rutas de acceso que son válidas en el sistema de archivos en el momento de la ejecución; **fopen** acepta rutas de acceso UNC y rutas de acceso que requieren unidades de red asignadas siempre y cuando el sistema que ejecuta el código tenga acceso al recurso compartido o a la unidad asignada en el momento de la ejecución. Cuando construya rutas de **fopen**, asegúrese de que las unidades, rutas de acceso o recursos compartidos de red estarán disponibles en el entorno de ejecución. Puede usar barras diagonales (/) o barras diagonales inversas (\\) como separadores de directorio en una ruta de acceso.

Compruebe siempre el valor devuelto para ver si el puntero es NULL antes de realizar ninguna otra operación en el archivo. Si se produce un error, se establece la variable global **errno** y se puede usar para obtener información específica del error. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="unicode-support"></a>Compatibilidad con Unicode

**fopen** admite secuencias de archivo Unicode. Para abrir un archivo Unicode, pase una marca de **CCS** que especifique la codificación deseada a **fopen**, como se indica a continuación.

> **FILE \*fp = fopen("newfile.txt", "rt+, ccs=** _encoding_ **");**

Los valores permitidos de *Encoding* son **Unicode**, **UTF-8**y **UTF-16LE**.

Cuando un archivo se abre en modo Unicode, las funciones de entrada traducen los datos leídos del archivo a datos UTF-16 almacenados como tipo **wchar_t**. Las funciones que escriben en un archivo abierto en modo Unicode esperan búferes que contienen datos UTF-16 almacenados como tipo **wchar_t**. Si el archivo está codificado como UTF-8, los datos UTF-16 se traducen a UTF-8 cuando se escriben, y el contenido codificado en UTF-8 del archivo se traduce a UTF-16 cuando se lee. Si se trata de leer o escribir un número impar de bytes en el modo Unicode, se producirá un error de [validación de parámetros](../../c-runtime-library/parameter-validation.md) . Para leer o escribir datos almacenados en el programa como UTF-8, use un modo de archivo binario o de texto en lugar de un modo Unicode. Cualquier traducción de codificación que sea necesaria es su responsabilidad.

Si el archivo ya existe y está abierto para lectura o para anexar, la marca de orden de bytes (BOM), si está presente en el archivo, determina la codificación. La codificación de BOM tiene prioridad sobre la codificación especificada por la marca **CCS** . La codificación **CCS** solo se usa cuando no hay Bom presente o el archivo es un archivo nuevo.

> [!NOTE]
> La detección de BOM solo se aplica a los archivos abiertos en modo Unicode (es decir, pasando la marca **CCS** ).

En la tabla siguiente se resumen los modos que se usan para las distintas marcas de **CCS** dadas a **fopen** y las marcas de orden de bytes en el archivo.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Codificaciones utilizadas basadas en el indicador de ccs y BOM

|marca de CCS|Ninguna BOM (o archivo nuevo)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Los archivos abiertos para escribir en el modo Unicode tienen una BOM escriba automáticamente.

Si el *modo* es **"a, CCS =** _Encoding_ **"** , **fopen** primero intenta abrir el archivo con acceso de lectura y escritura. Si esto se realiza correctamente, la función lee la BOM para determinar la codificación del archivo; si da error, la función utiliza la codificación predeterminada del archivo. En cualquier caso, **fopen** volverá a abrir el archivo con acceso de solo escritura. (Esto solo se aplica al modo **"a"** , no al modo **"a +"** ).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen**|**fopen**|**fopen**|**_wfopen**|

El *modo* de cadena de caracteres especifica el tipo de acceso solicitado para el archivo, como se indica a continuación.

|*mode*|Access|
|-|-|
| **"r"** | Abre para lectura. Si el archivo no existe o no se encuentra, se produce un error en la llamada **fopen** . |
| **"w"** | Abre un archivo vacío para escritura. Si el archivo especificado existe, se destruye su contenido. |
| **"a"** | Abre para escritura al final del archivo (anexo) sin eliminar el marcador de fin de archivo (EOF) antes de que se escriban nuevos datos en el archivo. Crea el archivo si no existe. |
| **"r+"** | Abre para lectura y escritura. El archivo debe existir. |
| **"w+"** | Abre un archivo vacío para lectura y escritura. Si el archivo existe, se destruye su contenido. |
| **"a+"** | Se abre para lectura y anexado. La operación de anexado incluye la eliminación del marcador EOF antes de que los nuevos datos se escriban en el archivo. El marcador EOF no se restablece una vez completada la escritura. Crea el archivo si no existe. |

Cuando un archivo se abre mediante el tipo de acceso **"a"** o el tipo de acceso **"a +"** , todas las operaciones de escritura se producen al final del archivo. El puntero de archivo se puede cambiar de posición mediante [fseek](fseek-fseeki64.md) o [rebobinar](rewind.md), pero siempre se mueve al final del archivo antes de que se realice cualquier operación de escritura. Por consiguiente, los datos existentes no pueden sobrescribirse.

El modo **"a"** no quita el marcador EOF antes de que se anexe al archivo. Una vez realizado el anexado, el comando TYPE de MS-DOS solo muestra los datos hasta el marcador EOF original, y no los datos anexados al archivo. Antes de que se anexe al archivo, el modo **"a +"** quita el marcador EOF. Después de anexar, el comando TYPE de MS-DOS muestra todos los datos del archivo. El modo **"a +"** es necesario para anexar a un archivo de secuencia que termina con el marcador EOF Ctrl + Z.

Cuando se especifica el tipo de acceso **"r +"** , **"w +"** o **"a +"** , se habilitan la lectura y la escritura (se dice que el archivo está abierto para "actualización"). Sin embargo, cuando cambie de lectura a la escritura, la operación de entrada debe encontrar un marcador EOF. Si no hay ningún EOF, debe utilizar una llamada intermedia a una función de posición del archivo. Las funciones de posición de archivo son **fsetpos**, [fseek](fseek-fseeki64.md)y [Rewind](rewind.md). Cuando cambie de escritura a lectura, debe usar una llamada intermedia a **fflush** o a una función de posicionamiento de archivo.

Además de los valores anteriores, los caracteres siguientes se pueden anexar al *modo* para especificar el modo de traducción de los caracteres de nueva línea.

|modificador de *modo*|Modo de traducción|
|-|-|
| **t** | Abra en modo de texto (traducido). |
| **b** | Abrir en modo binario (sin traducir); se suprimen las traducciones que implican caracteres de retorno de carro y avance de línea. |

En el modo de texto, CTRL + Z se interpreta como un carácter EOF en la entrada. En los archivos abiertos para lectura/escritura mediante **"a +"** , **FOPEN** comprueba un Ctrl + Z al final del archivo y lo quita, si es posible. Esto se hace porque el uso de [fseek](fseek-fseeki64.md) y **ftell** para desplace dentro de un archivo que finaliza con Ctrl + Z puede hacer que [fseek](fseek-fseeki64.md) se comporte de forma incorrecta cerca del final del archivo.

En el modo de texto, las combinaciones de retorno de carro y avance de línea se traducen en fuentes de una sola línea en la entrada, y los caracteres de avance de línea se traducen en combinaciones de retorno de carro y avance de línea en la salida. Cuando una función de E/S de flujo Unicode funciona en el modo de texto (valor predeterminado), se asume que el flujo de origen o de destino son una secuencia de caracteres multibyte. Por consiguiente, las funciones de entrada de secuencias Unicode convierten los caracteres multibyte en caracteres anchos (como si se realizara una llamada a la función **mbtowc**). Por la misma razón, las funciones de salida de secuencias Unicode convierten los caracteres anchos en caracteres multibyte (como si se realizara una llamada a la función **wctomb**).

Si **t** o **b** no se especifican en el *modo*, el modo de traducción predeterminado se define mediante la variable global [_fmode](../../c-runtime-library/fmode.md). Si **t** o **b** tiene como prefijo el argumento, la función produce un error y devuelve **null**.

Para más información sobre cómo utilizar los modos binario y de texto en Unicode y la E/S de flujo multibyte, vea [Text and Binary Mode File I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) y [E/S de secuencias Unicode en los modos binario y de texto](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

Las siguientes opciones se pueden anexar al *modo* para especificar comportamientos adicionales.

|modificador de *modo*|Comportamiento|
|-|-|
| **c** | Habilite la marca de confirmación para el *nombre de archivo* asociado para que el contenido del búfer de archivo se escriba directamente en el disco si se llama a **fflush** o **_flushall** . |
| **n** | Restablezca la marca de confirmación para el *nombre de archivo* asociado a "no-commit". Este es el valor predeterminado. También invalida la marca global de confirmación si vincula el programa a COMMODE.OBJ. El valor predeterminado de la marca de confirmación global es "no-commit", a menos que vincule explícitamente el programa a COMMODE.OBJ (vea [Link Options](../../c-runtime-library/link-options.md)). |
| **N** | Especifica que el archivo no se hereda mediante procesos secundarios. |
| **S** | Especifica que el almacenamiento en caché está optimizado para el acceso secuencial (pero no restringido a este) desde el disco. |
| **R** | Especifica que el almacenamiento en caché está optimizado para el acceso aleatorio (pero no restringido a este) desde el disco. |
| **T** | Especifica un archivo como temporal. Si es posible, no se vuelca en el disco. |
| **D** | Especifica un archivo como temporal. Se elimina cuando se cierra el puntero del último archivo. |
| **ccs=** _encoding_ | Especifica el juego de caracteres codificado que se va a usar (uno de **UTF-8**, **UTF-16LE**o **Unicode**) para este archivo. Deje sin especificar si desea la codificación ANSI. |

Los caracteres válidos para la cadena de *modo* que se usa en **fopen** y **_fdopen** se corresponden con los argumentos *Oflag* que se usan en _ [Open](open-wopen.md) y [_sopen](sopen-wsopen.md), como se indica a continuación.

|Caracteres en cadena de *modo*|Valor de *Oflag* equivalente \_para Open\_/sopen|
|-------------------------------|----------------------------------------------------|
|**a**|**\_O\_** &#124; &#124; **WRONLY o\_Append(normalmenteoWRONLYocrear)\_**  **\_\_** &#124;  **\_\_**  **\_ O\_anexar**)|
|**a+**|**\_O\_** &#124; &#124; **RDWR anexar\_(normalmenteo\_** **anexar o RDWR\_)\_**  **\_\_** &#124;  **\_ O\_crear** )|
|**r**|**\_O\_RDONLY**|
|**r+**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** (normalmente  **\_oWRONLY\_** &#124; &#124; o trunc **) \_\_**  **\_\_**|
|**w+**|**\_O\_RDWR** (normalmente  **\_oRDWR\_** &#124; &#124; o trunc **) \_\_**  **\_\_**|
|**b**|**\_BINARIO O\_**|
|**t**|**\_O\_TEXT**|
|**c**|None|
|**n**|None|
|**S**|**\_O\_SECUENCIAL**|
|**R**|**\_O\_ALEATORIO**|
|**T**|**\_O\_SHORTLIVED**|
|**D**|**\_O\_TEMPORAL**|
|**CCS = Unicode**|**\_O\_WTEXT**|
|**ccs=UTF-8**|**\_O\_UTF8**|
|**CCS = UTF-16LE**|**\_O\_UTF16**|

Si usa el modo **RB** , no tiene que trasladar el código y, si espera leer la mayor parte de un archivo grande o no le preocupa el rendimiento de la red, también puede considerar si usar archivos Win32 asignados a la memoria como una opción.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fopen**|\<stdio.h>|
|**_wfopen**|\<stdio.h> o \<wchar.h>|

**_wfopen** es una extensión de Microsoft. Para obtener más información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

Las opciones de *modo* **c**, **n**, **t**, **S**, **R**, **t**y **D** son extensiones de Microsoft para **fopen** y **_fdopen** y no deben usarse cuando se desea la portabilidad ANSI.

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
