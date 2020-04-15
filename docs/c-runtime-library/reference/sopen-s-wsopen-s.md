---
title: _sopen_s, _wsopen_s
ms.date: 4/2/2020
api_name:
- _sopen_s
- _wsopen_s
- _o__sopen_s
- _o__wsopen_s
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
- _sopen_s
- wsopen_s
- _wsopen_s
- sopen_s
helpviewer_keywords:
- sopen_s function
- _wsopen_s function
- wsopen_s function
- opening files, for sharing
- files [C++], opening
- _sopen_s function
- files [C++], sharing
ms.assetid: 059a0084-d08c-4973-9174-55e391b72aa2
ms.openlocfilehash: 81feacae0e4608512e7325c57e7f2b96bcf2cdde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356502"
---
# <a name="_sopen_s-_wsopen_s"></a>_sopen_s, _wsopen_s

Abre un archivo para compartirlo. Estas versiones de [_sopen y _wsopen](sopen-wsopen.md) incluyen mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _sopen_s(
   int* pfh,
   const char *filename,
   int oflag,
   int shflag,
   int pmode
);
errno_t _wsopen_s(
   int* pfh,
   const wchar_t *filename,
   int oflag,
   int shflag,
   int pmode,
);
```

### <a name="parameters"></a>Parámetros

*Pfh*<br/>
Identificador de archivo, o -1 si se produce un error.

*Nombre*<br/>
Nombre de archivo.

*oflag*<br/>
Tipo de operaciones permitido.

*shflag*<br/>
Tipo de uso compartido permitido.

*pmode*<br/>
Configuración de permisos.

## <a name="return-value"></a>Valor devuelto

Un valor devuelto distinto de cero indica un error; en ese caso **errno** se establece en uno de los siguientes valores.

|valor de errno|Condición|
|-|-|
| **EACCES** |  La ruta de acceso proporcionada es un directorio o el archivo es de solo lectura, pero se intentó realizar una operación de abrir para escribir. |
| **EEXIST** |  **_O_CREAT** y **_O_EXCL** se especificaron los indicadores, pero *el nombre* de archivo ya existe. |
| **EINVAL** |  El argumento *oflag*, *shflag*o *pmode* no válido, o *pfh* o *filename* era un puntero nulo. |
| **EMFILE** | No hay más descriptores de archivo disponibles. |
| **ENOENT** | No se encuentra el archivo o la ruta de acceso. |

Si se pasa un argumento no válido a la función, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y se devuelve **EINVAL.**

Para más información sobre estos y otros códigos devueltos, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

En el caso de un error, -1 se devuelve a través de *pfh* (a menos que *pfh* sea un puntero nulo).

## <a name="remarks"></a>Observaciones

La función **_sopen_s** abre el archivo especificado por *filename* y prepara el archivo para la lectura o escritura compartida, tal como se define por *oflag* y *shflag*. **_wsopen_s** es una versión de caracteres anchos de **_sopen_s;** el argumento *filename* que **se va** a _wsopen_s es una cadena de caracteres anchos. **_wsopen_s** y **_sopen_s** comportarse de forma idéntica de lo contrario.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen_s**|**_sopen_s**|**_sopen_s**|**_wsopen_s**|

La expresión entera *oflag* se forma combinando una o \<más constantes de manifiesto, que se definen en fcntl.h>. Cuando dos o más constantes forman el argumento *oflag*, se combinan con el operador OR bit a bit ( **&#124;** ).

|*oflag* constante|Comportamiento|
|-|-|
| **_O_APPEND** | Mueve un puntero de archivo al final del archivo antes de cada operación de escritura. |
| **_O_BINARY** | Abre el archivo en modo binario (sin traducir). (Vea [fopen](fopen-wfopen.md) para ver una descripción del modo binario.) |
| **_O_CREAT** | Crea un archivo y lo abre para escribir en él. No tiene ningún efecto si el archivo especificado por *filename* existe. El argumento *pmode* es necesario cuando se especifica **_O_CREAT.** |
| **_O_SHORT_LIVED _O_CREAT** **&#124;** | Crea un archivo temporal y, si es posible, no se vuelca en el disco. El argumento *pmode* es necesario cuando se especifica **_O_CREAT.** |
| **_O_TEMPORARY _O_CREAT** **&#124;** | Crea un archivo temporal. El archivo se elimina cuando se cierra el último descriptor de archivo. El argumento *pmode* es necesario cuando se especifica **_O_CREAT.** |
| **_O_CREAT** &#124;`_O_EXCL` | Devuelve un valor de error si existe un archivo especificado por *filename.* Solo se aplica cuando se utiliza con **_O_CREAT**. |
| **_O_NOINHERIT** | Impide que se cree un descriptor de archivo compartido. |
| **_O_RANDOM** | Especifica que el almacenamiento en caché está optimizado para el acceso aleatorio (pero no restringido a este) desde el disco. |
| **_O_RDONLY** | Abre un archivo únicamente para leerlo. No se puede especificar con **_O_RDWR** o **_O_WRONLY**. |
| **_O_RDWR** | Abre un archivo tanto para lectura como para escritura. No se puede especificar con **_O_RDONLY** o **_O_WRONLY**. |
| **_O_SEQUENTIAL** | Especifica que el almacenamiento en caché está optimizado para el acceso secuencial (pero no restringido a este) desde el disco. |
| **_O_TEXT** | Abre un archivo en modo de texto (traducido). (Para obtener más información, vea [E/S de archivo en modo binario y de texto](../../c-runtime-library/text-and-binary-mode-file-i-o.md) y [fopen](fopen-wfopen.md)). |
| **_O_TRUNC** | Abre un archivo y lo trunca a longitud cero. El archivo debe tener permiso de escritura. No se puede especificar con **_O_RDONLY**. **_O_TRUNC** utiliza con **_O_CREAT** abre un archivo existente o crea un archivo. **Nota:** El **indicador _O_TRUNC** destruye el contenido del archivo especificado. |
| **_O_WRONLY** | Abre un archivo únicamente para escribir en él. No se puede especificar con **_O_RDONLY** o **_O_RDWR**. |
| **_O_U16TEXT** | Abre un archivo en modo Unicode UTF-16. |
| **_O_U8TEXT** | Abre un archivo en modo Unicode UTF-8. |
| **_O_WTEXT** | Abre un archivo en modo Unicode. |

Para especificar el modo de acceso a archivos, debe especificar **_O_RDONLY**, **_O_RDWR**o **_O_WRONLY**. No existe un valor predeterminado para el modo de acceso.

Cuando se abre un archivo en modo Unicode mediante **_O_WTEXT**, **_O_U8TEXT**o **_O_U16TEXT**, las funciones de entrada traducen los datos que se leen del archivo a datos UTF-16 almacenados como tipo **wchar_t**. Las funciones que escriben en un archivo abierto en modo Unicode esperan búferes que contengan datos UTF-16 almacenados como tipo **wchar_t**. Si el archivo está codificado como UTF-8, los datos UTF-16 se traducen a UTF-8 cuando se escriben, y el contenido codificado en UTF-8 del archivo se traduce a UTF-16 cuando se lee. Si se intenta leer o escribir un número impar de bytes en el modo Unicode, se producirá un error de validación de parámetros. Para leer o escribir datos almacenados en el programa como UTF-8, use un modo de archivo binario o de texto en lugar de un modo Unicode. Cualquier traducción de codificación que sea necesaria es su responsabilidad.

Si se llama **a _sopen_s** con **_O_WRONLY** | **_O_APPEND** (modo de anexar) y **_O_WTEXT**, **_O_U16TEXT**, o **_O_U8TEXT**, primero intenta abrir el archivo para leer y escribir, leer la LDM y, a continuación, volver a abrirlo solo para escribirlo. Si no se puede abrir el archivo para lectura y escritura, abre el archivo solamente para escritura y usa el valor predeterminado como opción del modo Unicode.

El argumento *shflag* es una expresión constante que consta de una \<de las siguientes constantes de manifiesto, que se definen en share.h>.

|*shflag* constante|Comportamiento|
|-|-|
| **_SH_DENYRW** | Deniega el acceso de lectura y escritura a un archivo. |
| **_SH_DENYWR** | Deniega el acceso de escritura a un archivo. |
| **_SH_DENYRD** | Deniega el acceso de lectura a un archivo. |
| **_SH_DENYNO** | Permite el acceso de lectura y escritura. |

El argumento *pmode* siempre es necesario, a diferencia **de _sopen**. Cuando se especifica **_O_CREAT**, si el archivo no existe, *pmode* especifica la configuración de permisos del archivo, que se establece cuando se cierra el nuevo archivo la primera vez. De lo contrario, *pmode* se omite. *pmode* es una expresión de enteros que contiene una o ambas de \<las constantes de manifiesto **_S_IWRITE** y **_S_IREAD**, que se definen en la> sys-stat.h . Cuando ambas constantes se proporcionan, se combinan con el operador bit a bit OR. El significado de *pmode* es el siguiente.

|*pmode*|Significado|
|-|-|
| **_S_IREAD** | Solo se permite la lectura. |
| **_S_IWRITE** | Escritura permitida. (De hecho, se permiten la lectura y escritura). |
| **_S_IREAD** **_S_IWRITE &#124;** | Lectura y escritura permitidas. |

Si no se ha concedido el permiso de escritura, el archivo será de solo lectura. En el sistema operativo Windows, todos los archivos se pueden leer; es decir, no se puede conceder permisos únicamente de escritura. Por lo tanto, los modos **_S_IWRITE** y **_S_IWRITE** **_S_IREAD** | son equivalentes.

**_sopen_s** aplica la máscara de permiso de archivo actual a *pmode* antes de establecer los permisos. (Vea [_umask](umask.md).)

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_sopen_s**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|
|**_wsopen_s**|\<io.h> o \<wchar.h>|\<fcntl.h>, \<sys/types.h>, \<sys/stat.h>, \<share.h>|

**_sopen_s** y **_wsopen_s** son extensiones de Microsoft. Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [_locking](locking.md).

## <a name="see-also"></a>Consulte también

[E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fsopen, _wfsopen](fsopen-wfsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
