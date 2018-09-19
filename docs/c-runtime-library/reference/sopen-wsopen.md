---
title: _sopen, _wsopen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _sopen
- _wsopen
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
- _wsopen
- wsopen
- _sopen
- _tsopen
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e8d7f7624dc8c521186aa697ad8825c77e0108f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418109"
---
# <a name="sopen-wsopen"></a>_sopen, _wsopen

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

Si *filename* o *oflag* es un **NULL** puntero, o si *oflag* o *shflag* no está dentro de un válido intervalo de valores, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven -1 y establecen **errno** a uno de los siguientes valores.

|valor de errno|Condición|
|-|-|
**EACCES**|La ruta de acceso proporcionada es un directorio o el archivo es de solo lectura, pero se intentó realizar una operación de abrir para escribir.
**EEXIST**|**_O_CREAT** y **_O_EXCL** se especificaron marcas, pero *filename* ya existe.
**EINVAL**|No válido *oflag* o *shflag* argumento.
**EMFILE**|No hay más descriptores de archivo disponibles.
**ENOENT**|El archivo o la ruta de acceso no se encuentra.

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_sopen** función abre el archivo especificado por *filename* y prepara el archivo para lectura o escritura, compartida tal como se define por *oflag* y *shflag* . **_wsopen** es una versión con caracteres anchos de **_sopen**; el *filename* argumento pasado a **_wsopen** es una cadena de caracteres anchos. **_wsopen** y **_sopen** se comportan exactamente igual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen**|**_sopen**|**_sopen**|**_wsopen**|

La expresión de entero *oflag* se forma combinando una o varias de las constantes de manifiesto siguientes, que se definen en \<fcntl.h >. Cuando dos o más constantes forman el argumento *oflag*, se combinan con el operador OR bit a bit ( **&#124;** ).

|*oflag* constante|Comportamiento|
|-|-|
**_O_APPEND**|Mueve un puntero de archivo al final del archivo antes de cada operación de escritura.
**_O_BINARY**|Abre el archivo en modo binario (sin traducir). (Vea [fopen](fopen-wfopen.md) para ver una descripción del modo binario.)
**_O_CREAT**|Crea un archivo y lo abre para escribir en él. No tiene ningún efecto si el archivo especificado por *filename* existe. El *pmode* argumento es obligatorio cuando **_O_CREAT** se especifica.
**_O_CREAT** &AMP;#124; **_O_SHORT_LIVED**|Crea un archivo temporal y, si es posible, no se vuelca en el disco. El *pmode* argumento es obligatorio cuando **_O_CREAT** se especifica.
**_O_CREAT** &AMP;#124; **_O_TEMPORARY**|Crea un archivo temporal. El archivo se elimina cuando se cierra el último descriptor de archivo. El *pmode* argumento es obligatorio cuando **_O_CREAT** se especifica.
**_O_CREAT**&AMP;#124; ` _O_EXCL`|Devuelve un valor de error si un archivo especificado por *filename* existe. Se aplica solo cuando se usa con **_O_CREAT**.
**_O_NOINHERIT**|Impide que se cree un descriptor de archivo compartido.
**_O_RANDOM**|Especifica que el almacenamiento en caché está optimizado para el acceso aleatorio (pero no restringido a este) desde el disco.
**_O_RDONLY**|Abre un archivo únicamente para leerlo. No se puede especificar con **_O_RDWR** o **_O_WRONLY**.
**_O_RDWR**|Abre un archivo tanto para lectura como para escritura. No se puede especificar con **_O_RDONLY** o **_O_WRONLY**.
**_O_SEQUENTIAL**|Especifica que el almacenamiento en caché está optimizado para el acceso secuencial (pero no restringido a este) desde el disco.
**_O_TEXT**|Abre un archivo en modo de texto (traducido). (Para obtener más información, vea [E/S de archivo en modo binario y de texto](../../c-runtime-library/text-and-binary-mode-file-i-o.md) y [fopen](fopen-wfopen.md)).
**_O_TRUNC**|Abre un archivo y lo trunca a longitud cero. El archivo debe tener permiso de escritura. No se puede especificar con **_O_RDONLY**. **_O_TRUNC** utilizar con **_O_CREAT** abre un archivo existente o crea un archivo. **Nota:** el **_O_TRUNC** marca destruye el contenido del archivo especificado.
**_O_WRONLY**|Abre un archivo únicamente para escribir en él. No se puede especificar con **_O_RDONLY** o **_O_RDWR**.
**_O_U16TEXT**|Abre un archivo en modo Unicode UTF-16.
**_O_U8TEXT**|Abre un archivo en modo Unicode UTF-8.
**_O_WTEXT**|Abre un archivo en modo Unicode.

Para especificar el modo de acceso de archivo, debe especificar **_O_RDONLY**, **_O_RDWR**, o **_O_WRONLY**. No existe un valor predeterminado para el modo de acceso.

Cuando se abre un archivo en modo Unicode mediante **_O_WTEXT**, **_O_U8TEXT**, o **_O_U16TEXT**, entrada funciones traducen los datos que se leen desde el archivo a datos UTF-16 almacenados como de tipo **wchar_t**. Las funciones que escriben en un archivo abierto en modo Unicode esperan que haya búferes que contengan datos UTF-16 almacenados como de tipo **wchar_t**. Si el archivo está codificado como UTF-8, los datos UTF-16 se traducen a UTF-8 cuando se escriben, y el contenido codificado en UTF-8 del archivo se traduce a UTF-16 cuando se lee. Si se intenta leer o escribir un número impar de bytes en el modo Unicode, se producirá un error de validación de parámetros. Para leer o escribir datos almacenados en el programa como UTF-8, use un modo de archivo binario o de texto en lugar de un modo Unicode. Cualquier traducción de codificación que sea necesaria es su responsabilidad.

Si **_sopen** se llama con **_O_WRONLY** | **_O_APPEND** (modo anexar) y **_O_WTEXT**, **_O_ U16TEXT**, o **_O_U8TEXT**, primero se intentará abrir el archivo para lectura y escritura, leer la lista de materiales, y vuelva a abrirlo solamente para escritura. Si no se puede abrir el archivo para lectura y escritura, abre el archivo solamente para escritura y usa el valor predeterminado como opción del modo Unicode.

El argumento *shflag* es una expresión constante compuesta por una de las constantes de manifiesto siguientes, que se definen en \<share.h >.

|*shflag* constante|Comportamiento|
|-|-|
**_SH_DENYRW**|Deniega el acceso de lectura y escritura a un archivo.
**_SH_DENYWR**|Deniega el acceso de escritura a un archivo.
**_SH_DENYRD**|Deniega el acceso de lectura a un archivo.
**_SH_DENYNO**|Permite el acceso de lectura y escritura.

El *pmode* se requiere el argumento solo cuando **_O_CREAT** se especifica. Si el archivo no existe, *pmode* especifica la configuración de permisos del archivo, que se establece cuando el nuevo archivo se cierra por primera vez. En caso contrario, *pmode* se omite. *pmode* es una expresión de entero que contiene una o ambas de las constantes de manifiesto **_S_IWRITE** y **_S_IREAD**, que se definen en \<sys\stat >. Cuando ambas constantes se proporcionan, se combinan con el operador bit a bit OR. El significado de *pmode* es como sigue.

|*pmode*|Significado|
|-|-|
**_S_IREAD**|Solo se permite la lectura.
**_S_IWRITE**|Escritura permitida. (De hecho, se permiten la lectura y escritura).
**_S_IREAD** &AMP;#124; **_S_IWRITE**|Lectura y escritura permitidas.

Si no se ha concedido el permiso de escritura, el archivo será de solo lectura. En el sistema operativo Windows, todos los archivos se pueden leer; es decir, no se puede conceder permisos únicamente de escritura. Por lo tanto, los modos **_S_IWRITE** y **_S_IREAD** | **_S_IWRITE** son equivalentes.

**_sopen** aplica la máscara de permisos de archivo actual a *pmode* antes de que se establecen los permisos. (Vea [_umask](umask.md).)

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_sopen**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|
|**_wsopen**|\<io.h> o \<wchar.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [_locking](locking.md).

## <a name="see-also"></a>Vea también

[E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fsopen, _wfsopen](fsopen-wfsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
