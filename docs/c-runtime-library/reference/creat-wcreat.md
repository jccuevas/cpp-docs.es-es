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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 379a4adbf17755341fed6a48c649afe29e150fe5
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912112"
---
# <a name="_creat-_wcreat"></a>_creat, _wcreat

Crea un nuevo archivo. **_creat** y **_wcreat** han quedado en desuso; en su lugar [, use _sopen_s _wsopen_s](sopen-s-wsopen-s.md) .

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

*extensión*<br/>
Nombre del nuevo archivo.

*pmode*<br/>
Configuración de permisos.

## <a name="return-value"></a>Valor devuelto

Estas funciones, si se ejecutan correctamente, devuelven un descriptor de archivo para el archivo creado. De lo contrario, las funciones devuelven-1 y establecen **errno** , tal como se muestra en la tabla siguiente.

|valor de **errno**|Descripción|
|---------------------|-----------------|
|**EACCES**|*filename* especifica un archivo de solo lectura existente o especifica un directorio en lugar de un archivo.|
|**EMFILE**|No hay más descriptores de archivo disponibles.|
|**ENOENT**|No se pudo encontrar el archivo especificado.|

Si *filename* es **null**, estas funciones invocan el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** en **EINVAL** y devuelven-1.

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

La función **_creat** crea un nuevo archivo o abre y trunca uno existente. **_wcreat** es una versión con caracteres anchos de **_creat**; el argumento *filename* para **_wcreat** es una cadena de caracteres anchos. **_wcreat** y **_creat** se comportan de manera idéntica.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

Si el archivo especificado por *filename* no existe, se crea un nuevo archivo con la configuración de permisos especificada y se abre para escritura. Si el archivo ya existe y su configuración de permisos permite la escritura, **_creat** trunca el archivo a la longitud 0, destruyendo el contenido anterior y lo abre para escritura. La configuración de permisos, *PMODE*, se aplica solo a los archivos recién creados. El nuevo archivo recibe la configuración de permisos especificada cuando se cierra por primera vez. La expresión de entero *PMODE* contiene una o las dos constantes de manifiesto **_S_IWRITE** y **_S_IREAD**, definidas en SYS\Stat.h. Cuando se proporcionan ambas constantes, se combinan con el operador OR bit a bit ( **&#124;** ). El parámetro *PMODE* se establece en uno de los valores siguientes.

|Value|Definición|
|-----------|----------------|
|**_S_IWRITE**|Escritura permitida.|
|**_S_IREAD**|Lectura permitida.|
|**_S_IREAD** &#124; **_S_IWRITE**|Lectura y escritura permitidas.|

Si no se ha concedido el permiso de escritura, el archivo será de solo lectura. Todos los archivos son siempre legibles; es decir, no es posible conceder permisos de solo escritura. Los modos **_S_IWRITE** y **_S_IREAD** | **_S_IWRITE** son equivalentes. Los archivos abiertos con **_creat** se abren siempre en modo de compatibilidad (vea [_sopen](sopen-wsopen.md)) con **_SH_DENYNO**.

**_creat** aplica la máscara de permisos de archivo actual a *PMODE* antes de establecer los permisos (vea [_umask](umask.md)). **_creat** se proporciona principalmente para la compatibilidad con bibliotecas anteriores. Una llamada a **_open** con **_O_CREAT** y **_O_TRUNC** en el parámetro *Oflag* es equivalente a **_creat** y es preferible para el nuevo código.

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
