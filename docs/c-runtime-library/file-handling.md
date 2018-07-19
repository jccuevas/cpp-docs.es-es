---
title: Control de archivos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.files
dev_langs:
- C++
helpviewer_keywords:
- files [C++], handling
- files [C++], opening
- files [C++], manipulating
ms.assetid: 48119e2e-e94f-4602-b08b-b72440f731d8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95971cceab5673755b33bd99c3365bee62610bf5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392203"
---
# <a name="file-handling"></a>Control de archivos

Use estas rutinas para crear, eliminar y controlar archivos, y para establecer y comprobar permisos de acceso a archivos.

Las bibliotecas en tiempo de ejecución de C tienen un límite de 512 para el número de archivos que pueden estar abiertos en un momento dado. Si se intenta abrir un número de descriptores de archivo o de flujos de archivo mayor que el máximo se produce un error del programa. Use [_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md) para cambiar este número.

## <a name="file-handling-routines-file-descriptor"></a>Rutinas de control de archivos (descriptor de archivos)

Estas rutinas operan sobre los archivos designados por un descriptor de archivos.

|Rutina|Use|
|-------------|---------|
|[_chsize](../c-runtime-library/reference/chsize.md),[_chsize_s](../c-runtime-library/reference/chsize-s.md)|Cambiar el tamaño del archivo|
|[_filelength, _filelengthi64](../c-runtime-library/reference/filelength-filelengthi64.md)|Obtener la longitud del archivo|
|[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)|Obtener información de estado del archivo en el descriptor|
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|Devolver el identificador de archivo del sistema operativo asociado al descriptor de archivo del tiempo de ejecución de C existente|
|[_isatty](../c-runtime-library/reference/isatty.md)|Comprobar el dispositivo de caracteres|
|[_locking](../c-runtime-library/reference/locking.md)|Bloquear partes del archivo|
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|Asociar el descriptor de archivo del tiempo de ejecución de C al identificador de archivo del sistema operativo existente|
|[_setmode](../c-runtime-library/reference/setmode.md)|Establecer el modo de traducción de archivo|

## <a name="file-handling-routines-path-or-filename"></a>Rutinas de control de archivos (ruta de acceso o nombre de archivo)

Estas rutinas operan sobre archivos especificados por una ruta de acceso o un nombre de archivo.

|Rutina|Usar|
|-------------|---------|
|[_access, _waccess](../c-runtime-library/reference/access-waccess.md), [_access_s, _waccess_s](../c-runtime-library/reference/access-s-waccess-s.md)|Comprobar la configuración de los permisos de archivo|
|[_chmod, _wchmod](../c-runtime-library/reference/chmod-wchmod.md)|Cambiar la configuración de los permisos de archivo|
|[_fullpath, _wfullpath](../c-runtime-library/reference/fullpath-wfullpath.md)|Expandir una ruta de acceso relativa al nombre de ruta de acceso absoluta|
|[_makepath, _wmakepath](../c-runtime-library/reference/makepath-wmakepath.md), [_makepath_s, _wmakepath_s](../c-runtime-library/reference/makepath-s-wmakepath-s.md)|Combinar componentes de ruta de acceso para formar una ruta de acceso única y completa|
|[_mktemp, _wmktemp](../c-runtime-library/reference/mktemp-wmktemp.md), [_mktemp_s, _wmktemp_s](../c-runtime-library/reference/mktemp-s-wmktemp-s.md)|Crear nombre de archivo único|
|[remove, _wremove](../c-runtime-library/reference/remove-wremove.md)|Eliminar archivo|
|[rename, _wrename](../c-runtime-library/reference/rename-wrename.md)|Cambiar nombre de archivo|
|[_splitpath, _wsplitpath](../c-runtime-library/reference/splitpath-wsplitpath.md), [_splitpath_s, _wsplitpath_s](../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)|Analizar los componentes de la ruta de acceso|
|[_stat, _stat64, _stati64, _wstat, _wstat64, _wstati64](../c-runtime-library/reference/stat-functions.md)|Obtener información de estado del archivo sobre el archivo con nombre|
|[_umask](../c-runtime-library/reference/umask.md), [_umask_s](../c-runtime-library/reference/umask-s.md)|Establecer la máscara de permisos predeterminada para los nuevos archivos creados por el programa|
|[_unlink, _wunlink](../c-runtime-library/reference/unlink-wunlink.md)|Eliminar archivo|

## <a name="file-handling-routines-open-file"></a>Rutinas de control de archivos (abrir archivo)

Estas rutinas abren archivos.

|Rutina|Usar|
|-------------|---------|
|[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|Abrir un archivo y devolver un puntero al archivo abierto|
|[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|Abrir un flujo con uso compartido de archivos y devolver un puntero al archivo abierto|
|[_open, _wopen](../c-runtime-library/reference/open-wopen.md)|Abrir un archivo y devolver un descriptor de archivo del archivo abierto|
|[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s, _wsopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|Abrir un archivo con el uso compartido de archivos y devolver un descriptor de archivo al archivo abierto|
|[_pipe](../c-runtime-library/reference/pipe.md)|Crear una canalización de lectura y escritura.|
|[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s, _wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|Reasignar un puntero de archivo|

Estas rutinas proporcionan una forma de cambiar la representación del archivo, que puede ser una estructura de `FILE`, un descriptor de archivo o un identificador de archivos de Win32.

|Rutina|Usar|
|-------------|---------|
|[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|Asociar un flujo a un archivo que se ha abierto previamente para E/S de bajo nivel y devolver un puntero al flujo abierta|
|[_fileno](../c-runtime-library/reference/fileno.md)|Obtener el descriptor de archivo asociado a un flujo|
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|Devolver el identificador de archivo del sistema operativo asociado al descriptor de archivo del tiempo de ejecución de C existente|
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|Asociar el descriptor de archivo del tiempo de ejecución de C al identificador de archivo del sistema operativo existente|

 Las siguientes funciones de Win32 también abren archivos y canalizaciones:

- [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858.aspx)

- [CreatePipe](http://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)

- [CreateNamedPipe](http://msdn.microsoft.com/library/windows/desktop/aa365150.aspx)

## <a name="see-also"></a>Vea también

[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Control de directorio](../c-runtime-library/directory-control.md)<br/>
[Llamadas del sistema](../c-runtime-library/system-calls.md)<br/>
