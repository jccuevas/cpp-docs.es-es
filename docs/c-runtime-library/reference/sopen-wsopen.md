---
title: _sopen, _wsopen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: aac10cebd0f967944403837283e9008b0b1047fc
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="sopen-wsopen"></a>_sopen, _wsopen
Abre un archivo para compartirlo. Hay disponibles versiones más seguras de estas funciones; vea [_sopen_s, _wsopen_s](../../c-runtime-library/reference/sopen-s-wsopen-s.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
  
#### <a name="parameters"></a>Parámetros  
 `filename`  
 Nombre de archivo.  
  
 `oflag`  
 Tipo de operaciones permitido.  
  
 `shflag`  
 Tipo de uso compartido permitido.  
  
 `pmode`  
 Configuración de permisos.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada una de estas funciones devuelve un descriptor de archivo correspondiente al archivo abierto.  
  
 Si `filename` o `oflag` es un puntero `NULL`, o bien si `oflag` o `shflag` no están dentro de un intervalo válido de valores, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven -1 y establecen `errno` en uno de los siguientes valores.  
  
 `EACCES`  
 La ruta de acceso proporcionada es un directorio o el archivo es de solo lectura, pero se intentó realizar una operación de abrir para escribir.  
  
 `EEXIST`  
Las marcas  `_O_CREAT` y `_O_EXCL` se han especificado, pero `filename` ya existe.  
  
 `EINVAL`  
 Argumentos `oflag` o `shflag` no válidos.  
  
 `EMFILE`  
 No hay más descriptores de archivo disponibles.  
  
 `ENOENT`  
 El archivo o la ruta de acceso no se encuentra.  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 La función `_sopen` abre el archivo especificado por `filename` y lo prepara para una lectura o escritura compartida, como establecen las marcas `oflag` y `shflag`. `_wsopen` es una versión con caracteres anchos de `_sopen`; el argumento `filename` para `_wsopen` es una cadena de caracteres anchos. Por lo demás, `_wsopen` y `_sopen` se comportan de forma idéntica.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tsopen`|`_sopen`|`_sopen`|`_wsopen`|  
  
 La expresión de entero `oflag` se forma combinando una o más de las siguientes constantes de manifiesto, que se definen en \<fcntl.h>. Cuando dos o más constantes forman el argumento `oflag`, se combinan con el operador bit a bit OR (`|`).  
  
 `_O_APPEND`  
 Recoloca un puntero de archivo al final del archivo antes de cada operación de escritura.  
  
 `_O_BINARY`  
 Abre un archivo en modo binario (sin traducir). (Vea [fopen](../../c-runtime-library/reference/fopen-wfopen.md) para ver una descripción del modo binario.)  
  
 `_O_CREAT`  
 Crea un archivo y lo abre para escribir en él. No tiene ningún efecto si el archivo especificado por `filename` existe. El argumento `pmode` es necesario cuando `_O_CREAT` se especifica.  
  
 `_O_CREAT | _O_SHORT_LIVED`  
 Crea un archivo temporal y, si es posible, no se vuelca en el disco. El argumento `pmode` es necesario cuando `_O_CREAT` se especifica.  
  
 `_O_CREAT | _O_TEMPORARY`  
 Crea un archivo temporal. El archivo se elimina cuando se cierra el último descriptor de archivo. El argumento `pmode` es necesario cuando `_O_CREAT` se especifica.  
  
 `_O_CREAT | _O_EXCL`  
 Devuelve un valor de error si un archivo especificado por `filename` existe. Válido únicamente cuando se usa con `_O_CREAT`.  
  
 `_O_NOINHERIT`  
 Impide que se cree un descriptor de archivo compartido.  
  
 `_O_RANDOM`  
 Especifica un acceso principalmente aleatorio desde el disco.  
  
 `_O_RDONLY`  
 Abre un archivo únicamente para leerlo. No se puede especificar con `_O_RDWR` o `_O_WRONLY`.  
  
 `_O_RDWR`  
 Abre un archivo tanto para lectura como para escritura. No se puede especificar con `_O_RDONLY` o `_O_WRONLY`.  
  
 `_O_SEQUENTIAL`  
 Especifica un acceso principalmente secuencial desde el disco.  
  
 `_O_TEXT`  
 Abre un archivo en modo de texto (traducido). (Para obtener más información, vea [E/S de archivo en modo binario y de texto](../../c-runtime-library/text-and-binary-mode-file-i-o.md) y [fopen](../../c-runtime-library/reference/fopen-wfopen.md)).  
  
 `_O_TRUNC`  
 Abre un archivo y lo trunca a longitud cero. El archivo debe tener permiso de escritura. No se puede especificar con `_O_RDONLY`. Cuando `_O_TRUNC` se usa con `_O_CREAT`, se abre un archivo existente o se crea uno.  
  
> [!NOTE]
>  La marca `_O_TRUNC` destruye el contenido del archivo especificado.  
  
 `_O_WRONLY`  
 Abre un archivo únicamente para escribir en él. No se puede especificar con `_O_RDONLY` o `_O_RDWR`.  
  
 `_O_U16TEXT`  
 Abre un archivo en modo Unicode UTF-16.  
  
 `_O_U8TEXT`  
 Abre un archivo en modo Unicode UTF-8.  
  
 `_O_WTEXT`  
 Abre un archivo en modo Unicode.  
  
 Para especificar el modo de acceso a archivos, se debe especificar `_O_RDONLY`, `_O_RDWR` o `_O_WRONLY`. No existe un valor predeterminado para el modo de acceso.  
  
 Cuando un archivo se abre en modo Unicode con `_O_WTEXT`, `_O_U8TEXT` o `_O_U16TEXT`, las funciones de entrada traducen los datos leídos de dicho archivo a datos UTF-16 almacenados como de tipo `wchar_t`. Las funciones que escriben en un archivo abierto en modo Unicode esperan que haya búferes que contengan datos UTF-16 almacenados como de tipo `wchar_t`. Si el archivo está codificado como UTF-8, los datos UTF-16 se traducen a UTF-8 cuando se escriben, y el contenido codificado en UTF-8 del archivo se traduce a UTF-16 cuando se lee. Si se intenta leer o escribir un número impar de bytes en el modo Unicode, se producirá un error de validación de parámetros. Para leer o escribir datos almacenados en el programa como UTF-8, use un modo de archivo binario o de texto en lugar de un modo Unicode. Cualquier traducción de codificación que sea necesaria es su responsabilidad.  
  
 Si se llama a `_sopen` con `_O_WRONLY | _O_APPEND` (modo Anexar) y `_O_WTEXT`, `_O_U16TEXT` o `_O_U8TEXT`, primero se intentará abrir el archivo para lectura y escritura, leer la BOM y, luego, volver a abrirlo únicamente para escritura. Si no se puede abrir el archivo para lectura y escritura, abre el archivo solamente para escritura y usa el valor predeterminado como opción del modo Unicode.  
  
 El argumento `shflag` es una expresión constante formada por una de las siguientes constantes de manifiesto, que se definen en \<share.h>.  
  
 `_SH_DENYRW`  
 Deniega el acceso de lectura y escritura a un archivo.  
  
 `_SH_DENYWR`  
 Deniega el acceso de escritura a un archivo.  
  
 `_SH_DENYRD`  
 Deniega el acceso de lectura a un archivo.  
  
 `_SH_DENYNO`  
 Permite el acceso de lectura y escritura.  
  
 El argumento `pmode` es necesario únicamente cuando `_O_CREAT` se especifica. Si el archivo no existe, `pmode` especifica la configuración de permisos del archivo, que se establece cuando el nuevo archivo se cierra por primera vez. De lo contrario, `pmode` se omite. `pmode` es una expresión de entero que contiene una o ambas constantes del manifiesto `_S_IWRITE` y `_S_IREAD`, definidas en \<sys\stat.h>. Cuando ambas constantes se proporcionan, se combinan con el operador bit a bit OR. El significado de `pmode` es el que se indica a continuación.  
  
 `_S_IWRITE`  
 Escritura permitida.  
  
 `_S_IREAD`  
 Lectura permitida.  
  
 `_S_IREAD | _S_IWRITE`  
 Lectura y escritura permitidas.  
  
 Si no se ha concedido el permiso de escritura, el archivo será de solo lectura. En el sistema operativo Windows, todos los archivos se pueden leer; es decir, no se puede conceder permisos únicamente de escritura. En consecuencia, los modos `_S_IWRITE` y `_S_IREAD | _S_IWRITE` son equivalentes.  
  
 `_sopen` aplica la máscara de permisos de archivo actual a `pmode` antes de que los permisos se hayan definido. (Vea [_umask](../../c-runtime-library/reference/umask.md).)  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|-------------|---------------------|---------------------|  
|`_sopen`|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|  
|`_wsopen`|\<io.h> o \<wchar.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [_locking](../../c-runtime-library/reference/locking.md).  
  
## <a name="see-also"></a>Vea también  
 [E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)   
 [_close](../../c-runtime-library/reference/close.md)   
 [_creat, _wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [fopen, _wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_fsopen, _wfsopen](../../c-runtime-library/reference/fsopen-wfsopen.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)
