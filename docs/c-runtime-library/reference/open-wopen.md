---
title: _open, _wopen
ms.date: 11/04/2016
api_name:
- _open
- _wopen
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 4ce6e9aebe5d058143ad737f9c9db5bb68b30b1f
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150736"
---
# <a name="_open-_wopen"></a>_open, _wopen

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

Cada una de estas funciones devuelve un descriptor de archivo correspondiente al archivo abierto. Un valor devuelto de-1 indica un error; en ese caso, **errno** se establece en uno de los valores siguientes.

|valor de errno|Condición|
|-|-|
| **EACCES** | Se intentó abrir un archivo de solo lectura para escribir en él, el modo de uso compartido del archivo no permite las operaciones especificadas o la ruta de acceso indicada es un directorio. |
| **EEXIST** | **_O_CREAT** y **_O_EXCL** marcas especificadas, pero el *nombre de archivo* ya existe. |
| **EINVAL** | Argumento *Oflag* o *PMODE* no válido. |
| **EMFILE** | No hay más descriptores de archivo disponibles (hay demasiados archivos abiertos). |
| **ENOENT** | No se encuentra el archivo o la ruta de acceso. |

Para obtener más información sobre estos y otros códigos de retorno, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

La función **_open** abre el archivo especificado por *filename* y lo prepara para lectura o escritura, tal y como se especifica en *Oflag*. **_wopen** es una versión con caracteres anchos de **_open**; el argumento *filename* para **_wopen** es una cadena de caracteres anchos. **_wopen** y **_open** se comportan de manera idéntica.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_topen**|**_open**|**_open**|**_wopen**|

*Oflag* es una expresión de entero formada por una o varias de las siguientes constantes de manifiesto o combinaciones de constantes, que se definen en \<fcntl. h >.

|*Oflag* constante)|Comportamiento|
|-|-|
| **_O_APPEND** | Mueve un puntero de archivo al final del archivo antes de cada operación de escritura. |
| **_O_BINARY** | Abre el archivo en modo binario (sin traducir). (Vea [fopen](fopen-wfopen.md) para ver una descripción del modo binario.) |
| **_O_CREAT** | Crea un archivo y lo abre para escribir en él. No tiene ningún efecto si el archivo especificado por *filename* existe. El argumento *PMODE* es necesario cuando se especifica **_O_CREAT** . |
| **_O_CREAT** &#124; **_O_SHORT_LIVED** | Crea un archivo temporal y, si es posible, no se vuelca en el disco. El argumento *PMODE* es necesario cuando se especifica **_O_CREAT** . |
| **_O_CREAT** &#124; **_O_TEMPORARY** | Crea un archivo temporal. El archivo se elimina cuando se cierra el último descriptor de archivo. El argumento *PMODE* es necesario cuando se especifica **_O_CREAT** . |
| **_O_CREAT** &#124; `_O_EXCL` | Devuelve un valor de error si existe un archivo especificado por *filename* . Solo se aplica cuando se usa con **_O_CREAT**. |
| **_O_NOINHERIT** | Impide que se cree un descriptor de archivo compartido. |
| **_O_RANDOM** | Especifica que el almacenamiento en caché está optimizado para el acceso aleatorio (pero no restringido a este) desde el disco. |
| **_O_RDONLY** | Abre un archivo únicamente para leerlo. No se puede especificar con **_O_RDWR** o **_O_WRONLY**. |
| **_O_RDWR** | Abre un archivo tanto para lectura como para escritura. No se puede especificar con **_O_RDONLY** o **_O_WRONLY**. |
| **_O_SEQUENTIAL** | Especifica que el almacenamiento en caché está optimizado para el acceso secuencial (pero no restringido a este) desde el disco. |
| **_O_TEXT** | Abre un archivo en modo de texto (traducido). (Para obtener más información, vea [E/S de archivo en modo binario y de texto](../../c-runtime-library/text-and-binary-mode-file-i-o.md) y [fopen](fopen-wfopen.md)). |
| **_O_TRUNC** | Abre un archivo y lo trunca a longitud cero. El archivo debe tener permiso de escritura. No se puede especificar con **_O_RDONLY**. **_O_TRUNC** utilizado con **_O_CREAT** abre un archivo existente o crea un archivo. **Nota:** La marca **_O_TRUNC** destruye el contenido del archivo especificado. |
| **_O_WRONLY** | Abre un archivo únicamente para escribir en él. No se puede especificar con **_O_RDONLY** o **_O_RDWR**. |
| **_O_U16TEXT** | Abre un archivo en modo Unicode UTF-16. |
| **_O_U8TEXT** | Abre un archivo en modo Unicode UTF-8. |
| **_O_WTEXT** | Abre un archivo en modo Unicode. |

Para especificar el modo de acceso a archivos, debe especificar **_O_RDONLY**, **_O_RDWR**o **_O_WRONLY**. No existe un valor predeterminado para el modo de acceso.

Si **_O_WTEXT** se usa para abrir un archivo para leerlo, **_open** lee el principio del archivo y busca una marca de orden de bytes (BOM). Si hay una BOM, el archivo se considera como UTF-8 o UTF-16LE (esto depende de la BOM). Si no hay BOM, el archivo se considera ANSI. Cuando un archivo se abre para escritura mediante **_O_WTEXT**, se usa UTF-16. Independientemente de la configuración anterior o de la marca de orden de bytes, si se utiliza **_O_U8TEXT** , el archivo siempre se abrirá como UTF-8; Si se utiliza **_O_U16TEXT** , el archivo siempre se abrirá como UTF-16.

Cuando un archivo se abre en modo Unicode mediante **_O_WTEXT**, **_O_U8TEXT**o **_O_U16TEXT**, las funciones de entrada traducen los datos que se leen del archivo a datos UTF-16 almacenados como tipo **wchar_t**. Las funciones que escriben en un archivo abierto en modo Unicode esperan búferes que contengan datos UTF-16 almacenados como de tipo **wchar_t**. Si el archivo está codificado como UTF-8, los datos UTF-16 se traducen a UTF-8 cuando se escriben, y el contenido codificado en UTF-8 del archivo se traduce a UTF-16 cuando se lee. Si se trata de leer o escribir un número impar de bytes en el modo Unicode, se producirá un error de validación de parámetros. Para leer o escribir datos almacenados en el programa como UTF-8, use un modo de archivo binario o de texto en lugar de un modo Unicode. Cualquier traducción de codificación que sea necesaria es su responsabilidad.

Si se llama a **_open** con **_O_WRONLY** |  **_O_APPEND** (modo append) y **_O_WTEXT**, **_O_U16TEXT**o **_O_U8TEXT**, primero intenta abrir el archivo para lectura y escritura, leer la marca Bom y volver a abrirlo únicamente para escritura. Si no se puede abrir el archivo para lectura y escritura, abre el archivo solamente para escritura y usa el valor predeterminado como opción del modo Unicode.

Cuando se usan dos o más constantes de manifiesto para formar el argumento *Oflag* , las constantes se combinan con el operador bit a bit or ( **&#124;** ). Para obtener una descripción sobre los modos de texto y binario, vea [E/S de archivo de modo binario y de texto](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

El argumento *PMODE* solo es necesario cuando se especifica **_O_CREAT** . Si el archivo ya existe, se omite *PMODE* . De lo contrario, *PMODE* especifica la configuración de permisos del archivo, que se establece cuando el nuevo archivo se cierra por primera vez. **_open** aplica la máscara de permisos de archivo actual a *PMODE* antes de que se establezcan los permisos. (Para obtener más información, vea [_umask](umask.md)). *PMODE* es una expresión de tipo entero que contiene una o las dos constantes de manifiesto siguientes, que se definen en \<sys\stat.h >.

|*pmode*|Significado|
|-|-|
| **_S_IREAD** | Solo se permite la lectura. |
| **_S_IWRITE** | Escritura permitida. (De hecho, se permiten la lectura y escritura). |
| **_S_IREAD** &#124; **_S_IWRITE** | Lectura y escritura permitidas. |

Cuando se proporcionan ambas constantes, se combinan con el operador bit a bit OR ( **&#124;** ). En Windows, todos los archivos se pueden leer; es decir, el permiso de solo escritura no está disponible. Por lo tanto, los modos **_S_IWRITE** y **_S_IREAD** |  **_S_IWRITE** son equivalentes.

Si se especifica un valor distinto de una combinación de **_S_IREAD** y **_S_IWRITE** para *PMODE*, aunque especifique un *PMODE* válido en otro sistema operativo, o si se especifica un valor distinto de los valores de *Oflag* permitidos, la función genera una aserción en modo de depuración e invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve-1 y establece **errno** en **EINVAL**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_open**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|
|**_wopen**|\<io.h> o \<wchar.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|

**_open** y **_wopen** son extensiones de Microsoft. Para más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

### <a name="output"></a>Output

```Output
Open succeeded on input file
Open succeeded on output file
```

## <a name="see-also"></a>Consulte también

[E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
