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
ms.openlocfilehash: f18b04cadfa80d7e0be193bbd552efe8486eeeda
ms.sourcegitcommit: fcc3aeb271449f8be80348740cffef39ba543407
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "82538602"
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

*extensión*<br/>
Nombre de archivo.

*mode*<br/>
Tipo de acceso permitido.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error. Consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos códigos de error.

### <a name="error-conditions"></a>Condiciones de error

|*pFile*|*extensión*|*mode*|Valor devuelto|Contenido de *pFile*|
|-------------|----------------|------------|------------------|------------------------|
|**NULL**|cualquiera|cualquiera|**EINVAL**|sin cambios|
|cualquiera|**NULL**|cualquiera|**EINVAL**|sin cambios|
|cualquiera|cualquiera|**NULL**|**EINVAL**|sin cambios|

## <a name="remarks"></a>Observaciones

Los archivos abiertos por **fopen_s** y **_wfopen_s** no se pueden compartir. Si necesita que un archivo se pueda compartir, use [_fsopen, _wfsopen](fsopen-wfsopen.md) con la constante de modo compartido adecuada, por ejemplo, **_SH_DENYNO** para el uso compartido de lectura/escritura.

La función **fopen_s** abre el archivo especificado por *filename*. **_wfopen_s** es una versión con caracteres anchos de **fopen_s**; los argumentos para **_wfopen_s** son cadenas de caracteres anchos. **_wfopen_s** y **fopen_s** se comportan de manera idéntica.

**fopen_s** acepta rutas de acceso que son válidas en el sistema de archivos en el momento de la ejecución; Las rutas de acceso UNC y las rutas de acceso que afectan a las unidades de red asignadas son aceptadas por **fopen_s** siempre que el sistema que ejecuta el código tenga acceso al recurso compartido o a la unidad de red asignada en el momento de la ejecución. Al construir rutas de acceso para **fopen_s**, no realice suposiciones sobre la disponibilidad de unidades, rutas de acceso o recursos compartidos de red en el entorno de ejecución. Puede usar barras diagonales (/) o barras diagonales inversas (\\) como separadores de directorio en una ruta de acceso.

Estas funciones validan sus parámetros. Si *pFile*, *filename*o *mode* es un puntero nulo, estas funciones generan una excepción de parámetro no válido, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md).

Compruebe siempre el valor devuelto para ver si la función se realizó correctamente antes de realizar cualquier otra operación en el archivo. Si se produce un error, se devuelve el código de error y se establece la variable global **errno** . Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="unicode-support"></a>Compatibilidad con Unicode

**fopen_s** admite secuencias de archivo Unicode. Para abrir un archivo Unicode nuevo o existente, pase una marca de *CCS* que especifique la codificación deseada que se va a **fopen_s**:

**fopen_s(&fp, "newfile.txt", "rw, ccs=**_encoding_**");**

Los valores permitidos de *Encoding* son **Unicode**, **UTF-8**y **UTF-16LE**. Si no se especifica ningún valor para la *codificación*, **fopen_s** usa la codificación ANSI.

Si el archivo ya existe y está abierto para lectura o para anexar, la marca de orden de bytes (BOM), si está presente en el archivo, determina la codificación. La codificación de BOM tiene prioridad sobre la codificación especificada por la marca *CCS* . La codificación *CCS* solo se usa cuando no hay Bom presente o si el archivo es un archivo nuevo.

> [!NOTE]
> La detección de BOM solo se aplica a los archivos abiertos en modo Unicode. es decir, pasando el marcador *CCS* .

En la tabla siguiente se resumen los modos de las distintas marcas de *CCS* que se proporcionan para **Fopen_s** y las marcas de orden de bytes en el archivo.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Codificaciones utilizadas basadas en el indicador de ccs y BOM

|marca de CCS|Ninguna BOM (o archivo nuevo)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

En los archivos que se abren para escribir en el modo Unicode se escribe una BOM automáticamente.

Si el *modo* es **"a, CCS =**_Encoding_**"**, **fopen_s** primero intenta abrir el archivo con acceso de lectura y escritura. Si la operación se realiza correctamente, la función lee la BOM para determinar la codificación del archivo; si se produce un error, la función usa la codificación predeterminada del archivo. En cualquier caso, **fopen_s** vuelve a abrir el archivo con acceso de solo escritura. (Esto solo se aplica a **un** modo, no **a +**).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen_s**|**fopen_s**|**fopen_s**|**_wfopen_s**|

El *modo* de cadena de caracteres especifica el tipo de acceso solicitado para el archivo, como se indica a continuación.

|*mode*|Acceso|
|-|-|
| **c** | Abre para lectura. Si el archivo no existe o no se encuentra, se produce un error en la llamada **fopen_s** . |
| **con** | Abre un archivo vacío para escritura. Si el archivo especificado existe, se destruye su contenido. |
| **un** | Abre para escritura al final del archivo (anexo) sin eliminar el marcador de fin de archivo (EOF) antes de que se escriban nuevos datos en el archivo. Crea el archivo si no existe. |
| **"r +"** | Abre para lectura y escritura. El archivo debe existir. |
| **"w +"** | Abre un archivo vacío para lectura y escritura. Si el archivo existe, se destruye su contenido. |
| **"a +"** | Se abre para lectura y anexado. La operación de anexado incluye la eliminación del marcador EOF antes de que los nuevos datos se escriban en el archivo. El marcador EOF no se restablece una vez completada la escritura. Crea el archivo si no existe. |

Cuando un archivo se abre mediante el tipo de acceso **"a"** o **"a +"** , todas las operaciones de escritura se producen al final del archivo. El puntero de archivo se puede cambiar de posición mediante [fseek](fseek-fseeki64.md) o [rebobinar](rewind.md), pero siempre se mueve al final del archivo antes de que se realice cualquier operación de escritura para que los datos existentes no se puedan sobrescribir.

El modo **"a"** no quita el marcador EOF antes de anexar al archivo. Una vez realizado el anexado, el comando TYPE de MS-DOS solo muestra los datos hasta el marcador EOF original, y no los datos anexados al archivo. El modo **"a +"** quita el marcador EOF antes de anexar al archivo. Después de anexar, el comando TYPE de MS-DOS muestra todos los datos del archivo. El modo **"a +"** es necesario para anexar a un archivo de secuencia que se termina con el marcador EOF Ctrl + Z.

Cuando se especifica el tipo de acceso **"r +"**, **"w +"** o **"a +"** , se permiten la lectura y la escritura. (Se dice que el archivo está abierto para "actualización"). Sin embargo, cuando se cambia de lectura a escritura, la operación de entrada debe encontrar un marcador EOF. Si no hay ningún EOF, debe usar una llamada intermedia a una función de posición del archivo. Las funciones de posición de archivo son **fsetpos**, [fseek](fseek-fseeki64.md)y [Rewind](rewind.md). Cuando cambie de escritura a lectura, debe usar una llamada intermedia a **fflush** o a una función de posicionamiento de archivo.

Además de los valores anteriores, los caracteres siguientes se pueden incluir en el *modo* para especificar el modo de traducción de los caracteres de nueva línea:

|modificador de *modo*|Modo de traducción|
|-|-|
| **h** | Abra en modo de texto (traducido). |
| **b** | Abrir en modo binario (sin traducir); se suprimen las traducciones que implican caracteres de retorno de carro y avance de línea. |

En el modo de texto (traducido), CTRL + Z se interpreta como un carácter de final de archivo en la entrada. En los archivos abiertos para lectura/escritura con **"a +"**, **fopen_s** comprueba si hay un Ctrl + Z al final del archivo y lo quita, si es posible. Esto se hace porque el uso de [fseek](fseek-fseeki64.md) y **ftell** para desplace dentro de un archivo que finaliza con Ctrl + Z puede hacer que [fseek](fseek-fseeki64.md) se comporte de forma incorrecta cerca del final del archivo.

Además, en modo de texto, las combinaciones de retorno de carro y avance de línea se traducen en fuentes de una sola línea en la entrada y los caracteres de avance de línea se traducen en combinaciones de retorno de carro y avance de línea en la salida. Cuando una función de E/S de flujo Unicode funciona en el modo de texto (valor predeterminado), se asume que el flujo de origen o de destino son una secuencia de caracteres multibyte. Por consiguiente, las funciones de entrada de secuencias Unicode convierten los caracteres multibyte en caracteres anchos (como si se realizara una llamada a la función **mbtowc**). Por la misma razón, las funciones de salida de secuencias Unicode convierten los caracteres anchos en caracteres multibyte (como si se realizara una llamada a la función **wctomb**).

Si **t** o **b** no se especifican en el *modo*, el modo de traducción predeterminado se define mediante la variable global [_fmode](../../c-runtime-library/fmode.md). Si **t** o **b** tiene como prefijo el argumento, la función produce un error y devuelve **null**.

Para obtener más información sobre el uso de los modos de texto y binario en E/S de secuencias Unicode y multibyte, consulte [E/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md) y [E/S de secuencias Unicode en los modos binario y de texto](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

|modificador de *modo*|Comportamiento|
|-|-|
| **unidad** | Habilite la marca de confirmación para el *nombre de archivo* asociado para que el contenido del búfer de archivo se escriba directamente en el disco si se llama a **fflush** o **_flushall** . |
| **n** | Restablezca la marca de confirmación para el *nombre de archivo* asociado a "no-commit". Este es el valor predeterminado. También invalida la marca global de confirmación si vincula el programa a COMMODE.OBJ. El valor predeterminado de la marca de confirmación global es "no-commit", a menos que vincule explícitamente el programa a COMMODE.OBJ (vea [Opciones de vínculo](../../c-runtime-library/link-options.md)). |
| **N** | Especifica que el archivo no se hereda mediante procesos secundarios. |
| **Seg** | Especifica que el almacenamiento en caché está optimizado para el acceso secuencial (pero no restringido a este) desde el disco. |
| **R** | Especifica que el almacenamiento en caché está optimizado para el acceso aleatorio (pero no restringido a este) desde el disco. |
| **T** | Especifica un archivo como temporal. Si es posible, no se vuelca en el disco. |
| **D** | Especifica un archivo como temporal. Se elimina cuando se cierra el puntero del último archivo. |
| **ccs=**_encoding_ | Especifica el juego de caracteres codificado que se va a usar (uno de **UTF-8**, **UTF-16LE**o **Unicode**) para este archivo. Deje sin especificar si desea la codificación ANSI. |

Los caracteres válidos para la cadena de *modo* utilizada en **fopen_s** y [_fdopen](fdopen-wfdopen.md) corresponden a los argumentos de *Oflag* usados en [_open](open-wopen.md) y [_sopen](sopen-wsopen.md), como se indica a continuación.

|Caracteres en cadena de *modo*|Valor de *Oflag* equivalente para _open/_sopen|
|-------------------------------|----------------------------------------------------|
|**un**|**_O_WRONLY** &#124; **_O_APPEND** (normalmente **_O_WRONLY** &#124; **_O_CREAT** &#124; **_O_APPEND)**|
|**a +**|**_O_RDWR** &#124; **_O_APPEND** (normalmente **_O_RDWR** &#124; **_O_APPEND** &#124; **_O_CREAT)**|
|**r**|**_O_RDONLY**|
|**r +**|**_O_RDWR**|
|**w**|**_O_WRONLY** (normalmente **_O_WRONLY** &#124; **_O_CREAT** &#124; **_O_TRUNC)**|
|**w +**|**_O_RDWR** (usually **_O_RDWR** &#124; **_O_CREAT** &#124; **_O_TRUNC**)|
|**b**|**_O_BINARY**|
|**h**|**_O_TEXT**|
|**unidad**|None|
|**n**|None|
|**Seg**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**CCS = Unicode**|**_O_WTEXT**|
|**ccs=UTF-8**|**_O_UTF8**|
|**CCS = UTF-16LE**|**_O_UTF16**|

Si usa el modo **RB** , no necesitará migrar el código y espera leer una gran cantidad de archivos y/o no preocuparse por el rendimiento de la red, los archivos de Win32 asignados a la memoria también podrían ser una opción.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fopen_s**|\<stdio.h>|
|**_wfopen_s**|\<stdio.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

Las opciones de *modo* **c**, **n**y **t** son extensiones de Microsoft para **fopen_s** y [_fdopen](fdopen-wfdopen.md) y no deben usarse cuando se desea la portabilidad ANSI.

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
