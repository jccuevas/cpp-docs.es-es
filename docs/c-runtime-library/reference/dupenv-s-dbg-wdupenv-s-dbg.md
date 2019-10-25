---
title: _dupenv_s_dbg, _wdupenv_s_dbg
ms.date: 11/04/2016
api_name:
- _dupenv_s_dbg
- _wdupenv_s_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tdupenv_s_dbg
- _dupenv_s_dbg
- _wdupenv_s_dbg
helpviewer_keywords:
- _tdupenv_s_dbg function
- dupenv_s_dbg function
- _wdupenv_s_dbg function
- environment variables
- tdupenv_s_dbg function
- wdupenv_s_dbg function
- _dupenv_s_dbg function
ms.assetid: e3d81148-e24e-46d0-a21d-fd87b5e6256c
ms.openlocfilehash: 6c61986184f93c6cf6e83b33f77dce2bd017cfae
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937679"
---
# <a name="_dupenv_s_dbg-_wdupenv_s_dbg"></a>_dupenv_s_dbg, _wdupenv_s_dbg

Obtiene un valor del entorno actual.  Versiones de [_dupenv_s, _wdupenv_s](dupenv-s-wdupenv-s.md) que asignan memoria con [_malloc_dbg](malloc-dbg.md) para proporcionar información de depuración adicional.

## <a name="syntax"></a>Sintaxis

```C
errno_t _dupenv_s_dbg(
   char **buffer,
   size_t *numberOfElements,
   const char *varname,
   int blockType,
   const char *filename,
   int linenumber
);
errno_t _wdupenv_s_dbg(
   wchar_t **buffer,
   size_t * numberOfElements,
   const wchar_t *varname,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parámetros

*buffer*<br/>
Búfer en el que se va a almacenar el valor de la variable.

*numberOfElements*<br/>
Tamaño del *búfer*.

*varname*<br/>
Nombre de la variable de entorno.

*blockType*<br/>
Tipo solicitado del bloque de memoria: _ **client_block** o **_NORMAL_BLOCK**.

*filename*<br/>
Puntero al nombre del archivo de código fuente o **null**.

*linenumber*<br/>
Número de línea del archivo de código fuente o **null**.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.

Estas funciones validan sus parámetros; Si *buffer* o *varname* es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones establecen **errno** en **EINVAL** y devuelven **EINVAL**.

Si estas funciones no pueden asignar suficiente memoria, establecen *buffer* en **null** y *numberOfElements* en 0, y devuelven **ENOMEM**.

## <a name="remarks"></a>Comentarios

Las funciones **_dupenv_s_dbg** y **_wdupenv_s_dbg** son idénticas **a _dupenv_s** y **_wdupenv_s** , salvo que, cuando se define **_ Debug** , estas funciones usan la versión de depuración de [malloc](malloc.md), [_ malloc_dbg](malloc-dbg.md), para asignar memoria para el valor de la variable de entorno. Para obtener información sobre las características de depuración de **_ malloc_dbg**, consulte [_ malloc_dbg](malloc-dbg.md).

En la mayoría de los casos, no es necesario llamar a estas funciones explícitamente en la mayoría. En su lugar, puede definir la marca _ **crtdbg_map_alloc**. Cuando se define _ **crtdbg_map_alloc** , las llamadas a **_dupenv_s** y **_wdupenv_s** se reasignan a **_dupenv_s_dbg** y **_Wdupenv_s_dbg**, respectivamente, con el *blockType* establecido en **_NORMAL_BLOCK**. Por lo tanto, no es necesario llamar a estas funciones explícitamente a menos que desee marcar los bloques del montón como _ **client_block**. Para obtener más información sobre los tipos de bloques, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s_dbg**|**_dupenv_s_dbg**|**_dupenv_s_dbg**|**_wdupenv_s_dbg**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_dupenv_s_dbg**|\<crtdbg.h>|
|**_wdupenv_s_dbg**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_dupenv_s_dbg.c
#include  <stdlib.h>
#include <crtdbg.h>

int main( void )
{
   char *pValue;
   size_t len;
   errno_t err = _dupenv_s_dbg( &pValue, &len, "pathext",
      _NORMAL_BLOCK, __FILE__, __LINE__ );
   if ( err ) return -1;
   printf( "pathext = %s\n", pValue );
   free( pValue );
   err = _dupenv_s_dbg( &pValue, &len, "nonexistentvariable",
      _NORMAL_BLOCK, __FILE__, __LINE__ );
   if ( err ) return -1;
   printf( "nonexistentvariable = %s\n", pValue );
   free( pValue ); // It's OK to call free with NULL
}
```

```Output
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl
nonexistentvariable = (null)
```

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[Constantes de entorno](../../c-runtime-library/environmental-constants.md)<br/>
[getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s, _wputenv_s](putenv-s-wputenv-s.md)<br/>
