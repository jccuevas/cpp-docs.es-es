---
title: _sopen, _wsopen
ms.date: 11/04/2016
api_name:
- _sopen
- _wsopen
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
- _wsopen
- wsopen
- _sopen
- _tsopen
helpviewer_keywords:
- sopen function
- sharing files
- opening files, for sharing
- _sopen function
- wsopen function
- files [C++], opening
- files [C++], sharing
- _wsopen function
ms.assetid: a9d4cccf-06e9-414d-96fa-453fca88cc1f
ms.openlocfilehash: 8a8bad8888e141e7be77cb605f4774722753bfb4
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150735"
---
# <a name="_sopen-_wsopen"></a>_sopen, _wsopen

Abre un archivo para compartirlo. Hay disponibles versiones más seguras de estas funciones: vea [_sopen_s, _wsopen_s](sopen-s-wsopen-s.md).

## <a name="syntax"></a>Sintaxis

```C
int _sopen(
   const char *filename,
   int oflag,
   int shflag [,
   int pmode ]
);
int _wsopen(
   const wchar_t *filename,
   int oflag,
   int shflag [,
   int pmode ]
);
```

### <a name="parameters"></a>Parámetros

*filename*<br/>
Nombre de archivo.

*oflag*<br/>
Tipo de operaciones permitido.

*shflag*<br/>
Tipo de uso compartido permitido.

*pmode*<br/>
Configuración de permisos.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un descriptor de archivo correspondiente al archivo abierto.

Si *filename* o *Oflag* es un puntero **nulo** , o si *Oflag* o *shflag* no están dentro de un intervalo válido de valores, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven-1 y establecen **errno** en uno de los valores siguientes.

|valor de errno|Condición|
|-|-|
| **EACCES** | La ruta de acceso proporcionada es un directorio o el archivo es de solo lectura, pero se intentó realizar una operación de abrir para escribir. |
| **EEXIST** | Se especificaron **_O_CREAT** y **_O_EXCL** marcas, pero el *nombre de archivo* ya existe. |
| **EINVAL** | Argumento *Oflag* o *shflag* no válido. |
| **EMFILE** | No hay más descriptores de archivo disponibles. |
| **ENOENT** | El archivo o la ruta de acceso no se encuentra. |

Para obtener más información sobre estos y otros códigos de retorno, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

La función **_sopen** abre el archivo especificado por *filename* y prepara el archivo para lectura o escritura compartida, tal como se define en *Oflag* y *shflag*. **_wsopen** es una versión con caracteres anchos de **_sopen**; el argumento *filename* para **_wsopen** es una cadena de caracteres anchos. **_wsopen** y **_sopen** se comportan de manera idéntica.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen**|**_sopen**|**_sopen**|**_wsopen**|

La expresión de entero *Oflag* se forma combinando una o varias de las constantes de manifiesto siguientes, que se definen en \<fcntl. h >. Cuando dos o más constantes forman el argumento *Oflag*, se combinan con el operador bit a bit or ( **&#124;** ).

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

Cuando un archivo se abre en modo Unicode mediante **_O_WTEXT**, **_O_U8TEXT**o **_O_U16TEXT**, las funciones de entrada traducen los datos que se leen del archivo a datos UTF-16 almacenados como tipo **wchar_t**. Las funciones que escriben en un archivo abierto en modo Unicode esperan búferes que contengan datos UTF-16 almacenados como de tipo **wchar_t**. Si el archivo está codificado como UTF-8, los datos UTF-16 se traducen a UTF-8 cuando se escriben, y el contenido codificado en UTF-8 del archivo se traduce a UTF-16 cuando se lee. Si se trata de leer o escribir un número impar de bytes en el modo Unicode, se producirá un error de validación de parámetros. Para leer o escribir datos almacenados en el programa como UTF-8, use un modo de archivo binario o de texto en lugar de un modo Unicode. Cualquier traducción de codificación que sea necesaria es su responsabilidad.

Si se llama a **_sopen** con **_O_WRONLY** |  **_O_APPEND** (modo append) y **_O_WTEXT**, **_O_U16TEXT**o **_O_U8TEXT**, primero intenta abrir el archivo para lectura y escritura, leer la marca Bom y volver a abrirlo únicamente para escritura. Si no se puede abrir el archivo para lectura y escritura, abre el archivo solamente para escritura y usa el valor predeterminado como opción del modo Unicode.

El argumento *shflag* es una expresión constante formada por una de las constantes de manifiesto siguientes, que se definen en \<share. h >.

|*shflag* constante)|Comportamiento|
|-|-|
| **_SH_DENYRW** | Deniega el acceso de lectura y escritura a un archivo. |
| **_SH_DENYWR** | Deniega el acceso de escritura a un archivo. |
| **_SH_DENYRD** | Deniega el acceso de lectura a un archivo. |
| **_SH_DENYNO** | Permite el acceso de lectura y escritura. |

El argumento *PMODE* solo es necesario cuando se especifica **_O_CREAT** . Si el archivo no existe, *PMODE* especifica la configuración de permisos del archivo, que se establece cuando el nuevo archivo se cierra por primera vez. De lo contrario, *PMODE* se omite. *PMODE* es una expresión de tipo entero que contiene una o las dos constantes de manifiesto **_S_IWRITE** y **_S_IREAD**, que se definen en \<sys\stat.h >. Cuando ambas constantes se proporcionan, se combinan con el operador bit a bit OR. El significado de *PMODE* es el siguiente.

|*pmode*|Significado|
|-|-|
| **_S_IREAD** | Solo se permite la lectura. |
| **_S_IWRITE** | Escritura permitida. (De hecho, se permiten la lectura y escritura). |
| **_S_IREAD** &#124; **_S_IWRITE** | Lectura y escritura permitidas. |

Si no se ha concedido el permiso de escritura, el archivo será de solo lectura. En el sistema operativo Windows, todos los archivos se pueden leer; es decir, no se puede conceder permisos únicamente de escritura. Por lo tanto, los modos **_S_IWRITE** y **_S_IREAD** |  **_S_IWRITE** son equivalentes.

**_sopen** aplica la máscara de permisos de archivo actual a *PMODE* antes de que se establezcan los permisos. (Vea [_umask](umask.md).)

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_sopen**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|
|**_wsopen**|\<io.h> o \<wchar.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|

Para más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [_locking](locking.md).

## <a name="see-also"></a>Consulte también

[E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fsopen, _wfsopen](fsopen-wfsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
