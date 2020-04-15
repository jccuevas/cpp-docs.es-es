---
title: _creat, _wcreat
ms.date: 4/2/2020
api_name:
- _creat
- _wcreat
- _o__creat
- _o__wcreat
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
- wcreat
- _wcreat
- _creat
- tcreat
- _tcreat
helpviewer_keywords:
- wcreat function
- _wcreat function
- files [C++], creating
- _creat function
- tcreat function
- creat function
- _tcreat function
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
ms.openlocfilehash: 18ecf78d2cbff3647eae912a1bb1b17d5340f185
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348336"
---
# <a name="_creat-_wcreat"></a>_creat, _wcreat

Crea un nuevo archivo. **_creat** y **_wcreat** han quedado en desuso; utilizar [_sopen_s, _wsopen_s](sopen-s-wsopen-s.md) en su lugar.

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

*Nombre*<br/>
Nombre del nuevo archivo.

*pmode*<br/>
Configuración de permisos.

## <a name="return-value"></a>Valor devuelto

Estas funciones, si se ejecutan correctamente, devuelven un descriptor de archivo para el archivo creado. De lo contrario, las funciones devuelven -1 y establecen **errno** como se muestra en la tabla siguiente.

|**ajuste errno**|Descripción|
|---------------------|-----------------|
|**EACCES**|*filename* especifica un archivo de solo lectura existente o especifica un directorio en lugar de un archivo.|
|**EMFILE**|No hay más descriptores de archivo disponibles.|
|**ENOENT**|No se pudo encontrar el archivo especificado.|

Si *filename* es **NULL**, estas funciones invocan el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno en** **EINVAL** y devuelven -1.

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

La función **_creat** crea un nuevo archivo o abre y trunca uno existente. **_wcreat** es una versión de caracteres anchos de **_creat;** el argumento *filename* que **se va** a _wcreat es una cadena de caracteres anchos. **_wcreat** y **_creat** comportarse de forma idéntica de lo contrario.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

Si el archivo especificado por *filename* no existe, se crea un nuevo archivo con la configuración de permiso especificada y se abre para su escritura. Si el archivo ya existe y su configuración de permisos permite escribir, **_creat** trunca el archivo a la longitud 0, destruyendo el contenido anterior y lo abre para escribirlo. La configuración de permisos, *pmode*, solo se aplica a los archivos recién creados. El nuevo archivo recibe la configuración de permisos especificada cuando se cierra por primera vez. La expresión de enteros *pmode* contiene una o ambas de las constantes de manifiesto **_S_IWRITE** y **_S_IREAD**, definidas en SYS-Stat.h. Cuando se dan ambas constantes, se unen con el operador o bit a bit ( **&#124;** ). El parámetro *pmode* se establece en uno de los siguientes valores.

|Value|Definición|
|-----------|----------------|
|**_S_IWRITE**|Escritura permitida.|
|**_S_IREAD**|Lectura permitida.|
|**_S_IREAD** **_S_IWRITE &#124;**|Lectura y escritura permitidas.|

Si no se ha concedido el permiso de escritura, el archivo será de solo lectura. Todos los archivos son siempre legibles; es decir, no es posible conceder permisos de solo escritura. Los modos **_S_IWRITE** y **_S_IWRITE** **_S_IREAD** | son equivalentes. Los archivos abiertos con **_creat** siempre se abren en modo de compatibilidad (consulte [_sopen](sopen-wsopen.md)) con **_SH_DENYNO**.

**_creat** aplica la máscara de permiso de archivo actual a *pmode* antes de establecer los permisos (consulte [_umask](umask.md)). **_creat** se proporciona principalmente por compatibilidad con bibliotecas anteriores. Una llamada a **_open** con **_O_CREAT** y **_O_TRUNC** en el parámetro *oflag* es equivalente a **_creat** y es preferible para el nuevo código.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_creat**|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|
|**_wcreat**|\<io.h> o \<wchar.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Consulte también

[E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_umask](umask.md)<br/>
