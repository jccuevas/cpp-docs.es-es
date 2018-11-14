---
title: _open, _wopen
ms.date: 11/04/2016
apiname:
- _open
- _wopen
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
- _wopen
- _topen
- _open
helpviewer_keywords:
- opening files, for file I/O
- topen function
- _open function
- _topen function
- _wopen function
- files [C++], opening
- wopen function
- open function
ms.assetid: 13f6a0c3-d1aa-450d-a7aa-74abc91b163e
ms.openlocfilehash: 7ef28d6cafa0b74b50ee2c50ec380b8bd3aed79f
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327296"
---
# <a name="open-wopen"></a>_open, _wopen

Abre un archivo. Estas funciones están en desuso porque hay disponibles versiones más seguras; vea [_sopen_s, _wsopen_s](sopen-s-wsopen-s.md).

## <a name="syntax"></a>Sintaxis

```C
int _open(
   const char *filename,
   int oflag [,
   int pmode]
);
int _wopen(
   const wchar_t *filename,
   int oflag [,
   int pmode]
);
```

### <a name="parameters"></a>Parámetros

*filename*<br/>
Nombre de archivo.

*oflag*<br/>
Tipo de operaciones permitido.

*pmode*<br/>
Modo de permiso.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un descriptor de archivo correspondiente al archivo abierto. Un valor devuelto de -1 indica un error; en ese caso **errno** se establece en uno de los siguientes valores.

|valor de errno|Condición|
|-|-|
| **EACCES** | Se intentó abrir un archivo de solo lectura para escribir en él, el modo de uso compartido del archivo no permite las operaciones especificadas o la ruta de acceso indicada es un directorio. |
| **EEXIST** | **_O_CREAT** y **_O_EXCL** marcas especificadas, pero *filename* ya existe. |
| **EINVAL** | No válido *oflag* o *pmode* argumento. |
| **EMFILE** | No hay más descriptores de archivo disponibles (hay demasiados archivos abiertos). |
| **ENOENT** | No se encuentra el archivo o la ruta de acceso. |

Para obtener más información sobre estos y otros códigos de retorno, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_open** función abre el archivo especificado por *filename* y prepararlo para la lectura o escritura, según lo especificado por *oflag*. **_wopen** es una versión con caracteres anchos de **_open**; el *filename* argumento **_wopen** es una cadena de caracteres anchos. **_wopen** y **_open** se comportan exactamente igual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_topen**|**_open**|**_open**|**_wopen**|

*oflag* es una expresión de entero formada por una o varias de las siguientes constantes de manifiesto o combinaciones de constantes, que se definen en \<fcntl.h >.

|*oflag* constante|Comportamiento|
|-|-|
| **_O_APPEND** | Mueve un puntero de archivo al final del archivo antes de cada operación de escritura. |
| **_O_BINARY** | Abre el archivo en modo binario (sin traducir). (Vea [fopen](fopen-wfopen.md) para ver una descripción del modo binario.) |
| **_O_CREAT** | Crea un archivo y lo abre para escribir en él. No tiene ningún efecto si el archivo especificado por *filename* existe. El *pmode* argumento es obligatorio cuando **_O_CREAT** se especifica. |
| **_O_CREAT** &AMP;#124; **_O_SHORT_LIVED** | Crea un archivo temporal y, si es posible, no se vuelca en el disco. El *pmode* argumento es obligatorio cuando **_O_CREAT** se especifica. |
| **_O_CREAT** &AMP;#124; **_O_TEMPORARY** | Crea un archivo temporal. El archivo se elimina cuando se cierra el último descriptor de archivo. El *pmode* argumento es obligatorio cuando **_O_CREAT** se especifica. |
| **_O_CREAT**&AMP;#124; ` _O_EXCL` | Devuelve un valor de error si un archivo especificado por *filename* existe. Se aplica solo cuando se usa con **_O_CREAT**. |
| **_O_NOINHERIT** | Impide que se cree un descriptor de archivo compartido. |
| **_O_RANDOM** | Especifica que el almacenamiento en caché está optimizado para el acceso aleatorio (pero no restringido a este) desde el disco. |
| **_O_RDONLY** | Abre un archivo únicamente para leerlo. No se puede especificar con **_O_RDWR** o **_O_WRONLY**. |
| **_O_RDWR** | Abre un archivo tanto para lectura como para escritura. No se puede especificar con **_O_RDONLY** o **_O_WRONLY**. |
| **_O_SEQUENTIAL** | Especifica que el almacenamiento en caché está optimizado para el acceso secuencial (pero no restringido a este) desde el disco. |
| **_O_TEXT** | Abre un archivo en modo de texto (traducido). (Para obtener más información, vea [E/S de archivo en modo binario y de texto](../../c-runtime-library/text-and-binary-mode-file-i-o.md) y [fopen](fopen-wfopen.md)). |
| **_O_TRUNC** | Abre un archivo y lo trunca a longitud cero. El archivo debe tener permiso de escritura. No se puede especificar con **_O_RDONLY**. **_O_TRUNC** utilizado con **_O_CREAT** abre un archivo existente o crea un archivo. **Nota:** el **_O_TRUNC** marca destruye el contenido del archivo especificado. |
| **_O_WRONLY** | Abre un archivo únicamente para escribir en él. No se puede especificar con **_O_RDONLY** o **_O_RDWR**. |
| **_O_U16TEXT** | Abre un archivo en modo Unicode UTF-16. |
| **_O_U8TEXT** | Abre un archivo en modo Unicode UTF-8. |
| **_O_WTEXT** | Abre un archivo en modo Unicode. |

Para especificar el modo de acceso de archivo, debe especificar **_O_RDONLY**, **_O_RDWR**, o **_O_WRONLY**. No existe un valor predeterminado para el modo de acceso.

Si **_O_WTEXT** se usa para abrir un archivo para leerlo, **_open** lee el principio del archivo y comprobar si hay una marca de orden de bytes (BOM). Si hay una BOM, el archivo se considera como UTF-8 o UTF-16LE (esto depende de la BOM). Si no hay BOM, el archivo se considera ANSI. Cuando se abre un archivo para escribir en él mediante **_O_WTEXT**, se usa UTF-16. Independientemente de cualquier configuración anterior BOM o, si **_O_U8TEXT** es utilizado, el archivo siempre se abrirá como UTF-8; si **_O_U16TEXT** es utilizado, el archivo siempre se abrirá como UTF-16.

Cuando se abre un archivo en modo Unicode mediante **_O_WTEXT**, **_O_U8TEXT**, o **_O_U16TEXT**, entrada funciones traducen los datos que se leen desde el archivo a datos UTF-16 almacena como tipo **wchar_t**. Las funciones que escriben en un archivo abierto en modo Unicode esperan que haya búferes que contienen datos UTF-16 almacenados como tipo **wchar_t**. Si el archivo está codificado como UTF-8, los datos UTF-16 se traducen a UTF-8 cuando se escriben, y el contenido codificado en UTF-8 del archivo se traduce a UTF-16 cuando se lee. Si se intenta leer o escribir un número impar de bytes en el modo Unicode, se producirá un error de validación de parámetros. Para leer o escribir datos almacenados en el programa como UTF-8, use un modo de archivo binario o de texto en lugar de un modo Unicode. Cualquier traducción de codificación que sea necesaria es su responsabilidad.

Si **_open** se llama con **_O_WRONLY** | **_O_APPEND** (modo anexar) y **_O_WTEXT**, **_O_ U16TEXT**, o **_O_U8TEXT**, primero intenta abrir el archivo para lectura y escritura, leer la lista de materiales, a continuación, vuelva a abrirlo únicamente para escritura. Si no se puede abrir el archivo para lectura y escritura, abre el archivo solamente para escritura y usa el valor predeterminado como opción del modo Unicode.

Cuando se usan dos o más constantes de manifiesto para formar el *oflag* argumento, estas constantes se combinan con el operador OR bit a bit ( **&#124;** ). Para obtener una descripción sobre los modos de texto y binario, vea [E/S de archivo de modo binario y de texto](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

El *pmode* argumento es obligatorio solo cuando **_O_CREAT** se especifica. Si el archivo ya existe, *pmode* se omite. En caso contrario, *pmode* especifica la configuración de permisos de archivo, que se establece cuando el nuevo archivo se cierra por primera vez. **_abrir** aplica la máscara de permisos de archivo actual a *pmode* antes de que se establecen los permisos. (Para obtener más información, consulte [_umask](umask.md).) *pmode* es una expresión de entero que contiene una o ambas de las siguientes constantes de manifiesto, que se definen en \<sys\stat >.

|*pmode*|Significado|
|-|-|
| **_S_IREAD** | Solo se permite la lectura. |
| **_S_IWRITE** | Escritura permitida. (De hecho, se permiten la lectura y escritura). |
| **_S_IREAD** &AMP;#124; **_S_IWRITE** | Lectura y escritura permitidas. |

Cuando ambas constantes se proporcionan, se unen con el operador OR bit a bit ( **&#124;** ). En Windows, todos los archivos se pueden leer; es decir, el permiso de solo escritura no está disponible. Por lo tanto, los modos **_S_IWRITE** y **_S_IREAD** | **_S_IWRITE** son equivalentes.

Si un valor distinto de cualquier combinación de **_S_IREAD** y **_S_IWRITE** se especifica para *pmode*, incluso si especificaría válido *pmode*en otro sistema operativo, o si cualquier valor distinto de los permitidos *oflag* se especifican valores, la función genera una aserción en modo de depuración e invoca el controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve -1 y establece **errno** a **EINVAL**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_open**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|
|**_wopen**|\<io.h> o \<wchar.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|

**_abrir** y **_wopen** son extensiones de Microsoft. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_open.c
// compile with: /W3
/* This program uses _open to open a file
* named CRT_OPEN.C for input and a file named CRT_OPEN.OUT
* for output. The files are then closed.
*/
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int fh1, fh2;

   fh1 = _open( "CRT_OPEN.C", _O_RDONLY ); // C4996
   // Note: _open is deprecated; consider using _sopen_s instead
   if( fh1 == -1 )
      perror( "Open failed on input file" );
   else
   {
      printf( "Open succeeded on input file\n" );
      _close( fh1 );
   }

   fh2 = _open( "CRT_OPEN.OUT", _O_WRONLY | _O_CREAT, _S_IREAD |
                            _S_IWRITE ); // C4996
   if( fh2 == -1 )
      perror( "Open failed on output file" );
   else
   {
      printf( "Open succeeded on output file\n" );
      _close( fh2 );
   }
}
```

### <a name="output"></a>Salida

```Output
Open succeeded on input file
Open succeeded on output file
```

## <a name="see-also"></a>Vea también

[E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
