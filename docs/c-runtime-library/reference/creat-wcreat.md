---
title: _creat, _wcreat | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _creat
- _wcreat
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
- wcreat
- _wcreat
- _creat
- tcreat
- _tcreat
dev_langs:
- C++
helpviewer_keywords:
- wcreat function
- _wcreat function
- files [C++], creating
- _creat function
- tcreat function
- creat function
- _tcreat function
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a6b987faa30439f0f374838fe7fcd4d942b8cc7
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
---
# <a name="creat-wcreat"></a>_creat, _wcreat

Crear un archivo nuevo. **_creat** y **_wcreat** han quedado en desuso; use [_sopen_s, _wsopen_s](sopen-s-wsopen-s.md) en su lugar.

## <a name="syntax"></a>Sintaxis

```C
int _creat(
   const char *filename,
   int pmode
);
int _wcreat(
   const wchar_t *filename,
   int pmode
);
```

### <a name="parameters"></a>Parámetros

*filename*<br/>
Nombre del nuevo archivo.

*pmode*<br/>
Configuración de permisos.

## <a name="return-value"></a>Valor devuelto

Estas funciones, si se ejecutan correctamente, devuelven un descriptor de archivo para el archivo creado. De lo contrario, las funciones devuelven -1 y establecen **errno** tal como se muestra en la tabla siguiente.

|**errno** configuración|Descripción|
|---------------------|-----------------|
|**EACCES**|*nombre de archivo* especifica un archivo de sólo lectura existente o especifica un directorio en lugar de un archivo.|
|**EMFILE**|No hay más descriptores de archivo disponibles.|
|**ENOENT**|No se pudo encontrar el archivo especificado.|

Si *filename* es **NULL**, estas funciones invocan el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** a **EINVAL** y devuelven -1.

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_creat** función crea un nuevo archivo o lo abre y trunca uno ya existente. **_wcreat** es una versión con caracteres anchos de **_creat**; el *filename* argumento pasado a **_wcreat** es una cadena de caracteres anchos. **_wcreat** y **_creat** se comportan exactamente igual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

Si el archivo especificado por *nombre de archivo* no existe, un nuevo archivo se crea con la configuración del permiso especificado y se abre para escribir en él. Si el archivo ya existe y su configuración de permisos permite escribir, **_creat** trunca la longitud del archivo hasta 0, destruir el contenido anterior y lo abre para escritura. La configuración del permiso, *pmode*, se aplica a solo los archivos recién creados. El nuevo archivo recibe la configuración de permisos especificada cuando se cierra por primera vez. La expresión de entero *pmode* contiene una o ambas de las constantes de manifiesto **_S_IWRITE** y **_S_IREAD**, definida en sys\stat. Cuando ambas constantes se proporcionan, se combinan con el bit a bit u operador ( **&#124;** ). El *pmode* parámetro se establece en uno de los siguientes valores.

|Valor|de esquema JSON|
|-----------|----------------|
|**_S_IWRITE**|Escritura permitida.|
|**_S_IREAD**|Lectura permitida.|
|**_S_IREAD** &AMP;#124; **_S_IWRITE**|Lectura y escritura permitidas.|

Si no se ha concedido el permiso de escritura, el archivo será de solo lectura. Todos los archivos son siempre legibles; es decir, no es posible conceder permisos de solo escritura. Los modos de **_S_IWRITE** y **_S_IREAD** | **_S_IWRITE** , a continuación, son equivalentes. Los archivos abiertos con **_creat** siempre se abren en modo de compatibilidad (vea [_sopen](sopen-wsopen.md)) con **_SH_DENYNO**.

**_creat** aplica la máscara de permisos de archivo actual a *pmode* antes de establecer los permisos (vea [_umask](umask.md)). **_creat** se proporciona principalmente por compatibilidad con bibliotecas anteriores. Una llamada a **_open** con **_O_CREAT** y **_O_TRUNC** en el *oflag* parámetro es equivalente al **_creat**y es preferible para el código nuevo.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_creat**|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|
|**_wcreat**|\<io.h> o \<wchar.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_creat.c
// compile with: /W3
// This program uses _creat to create
// the file (or truncate the existing file)
// named data and open it for writing.

#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int fh;

   fh = _creat( "data", _S_IREAD | _S_IWRITE ); // C4996
   // Note: _creat is deprecated; use _sopen_s instead
   if( fh == -1 )
      perror( "Couldn't create data file" );
   else
   {
      printf( "Created data file.\n" );
      _close( fh );
   }
}
```

```Output
Created data file.
```

## <a name="see-also"></a>Vea también

[E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_umask](umask.md)<br/>
