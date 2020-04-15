---
title: _dupenv_s, _wdupenv_s
ms.date: 4/2/2020
api_name:
- _dupenv_s
- _wdupenv_s
- _o__dupenv_s
- _o__wdupenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tdupenv_s
- _dupenv_s
- wdupenv_s
- dupenv_s
- _tdupenv_s
- _wdupenv_s
helpviewer_keywords:
- _dupenv_s function
- _tdupenv_s function
- _wdupenv_s function
- environment variables
- wdupenv_s function
- dupenv_s function
- tdupenv_s function
ms.assetid: b729ecc2-a31d-4ccf-92a7-5accedb8f8c8
ms.openlocfilehash: f65f1da3e8cef077df04d0bdb7eb2aaf75afd9fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348058"
---
# <a name="_dupenv_s-_wdupenv_s"></a>_dupenv_s, _wdupenv_s

Obtiene un valor del entorno actual.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _dupenv_s(
   char **buffer,
   size_t *numberOfElements,
   const char *varname
);
errno_t _wdupenv_s(
   wchar_t **buffer,
   size_t *numberOfElements,
   const wchar_t *varname
);
```

### <a name="parameters"></a>Parámetros

*Búfer*<br/>
Búfer en el que se va a almacenar el valor de la variable.

*numberOfElements*<br/>
Tamaño del *búfer*.

*Varname*<br/>
Nombre de la variable de entorno.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.

Estas funciones validan sus parámetros; si *buffer* o *varname* es **NULL**, se invoca el controlador de parámetros no válidos como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones establecen **errno en** **EINVAL** y devuelven **EINVAL**.

Si estas funciones no pueden asignar suficiente memoria, establecen *buffer* en **NULL** y *numberOfElements* en 0 y devuelven **ENOMEM**.

## <a name="remarks"></a>Observaciones

La función **_dupenv_s** busca *varname*en la lista de variables de entorno. Si se encuentra la variable, **_dupenv_s** asigna un búfer y copia el valor de la variable en el búfer. La dirección y la longitud del búfer se devuelven en *buffer* y *numberOfElements*. Al asignar el búfer en sí, **_dupenv_s** proporciona una alternativa más conveniente a [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

> [!NOTE]
> Es responsabilidad del programa de llamada liberar memoria llamando a [free](free.md).

Si no se encuentra la variable, *el búfer* se establece en **NULL**, *numberOfElements* se establece en 0 y el valor devuelto es 0 porque esta situación no se considera una condición de error.

Si no está interesado en el tamaño del búfer, puede pasar **NULL** para *numberOfElements*.

**_dupenv_s** no distingue mayúsculas de minúsculas en el sistema operativo Windows. **_dupenv_s** utiliza la copia del entorno al que señala la variable global **_environ** para tener acceso al entorno. Consulte las Observaciones en [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md) para un análisis de **_environ**.

El valor en *el búfer* es una copia del valor de la variable de entorno; modificarlo no tiene ningún efecto sobre el medio ambiente. Use la función [_putenv_s, _wputenv_s](putenv-s-wputenv-s.md) para modificar el valor de una variable de entorno.

**_wdupenv_s** es una versión de caracteres anchos de **_dupenv_s;** los argumentos de **_wdupenv_s** son cadenas de caracteres anchos. La variable global **_wenviron** es una versión de caracteres anchos de **_environ**. Consulte las _wgetenv_s Comentarios en [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md) para obtener más información sobre **_wenviron**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s**|**_dupenv_s**|**_dupenv_s**|**_wdupenv_s**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_dupenv_s**|\<stdlib.h>|
|**_wdupenv_s**|\<stdlib.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_dupenv_s.c
#include  <stdlib.h>

int main( void )
{
   char *pValue;
   size_t len;
   errno_t err = _dupenv_s( &pValue, &len, "pathext" );
   if ( err ) return -1;
   printf( "pathext = %s\n", pValue );
   free( pValue );
   err = _dupenv_s( &pValue, &len, "nonexistentvariable" );
   if ( err ) return -1;
   printf( "nonexistentvariable = %s\n", pValue );
   free( pValue ); // It's OK to call free with NULL
}
```

```Output
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl
nonexistentvariable = (null)
```

## <a name="see-also"></a>Consulte también

[Control de Procesos y Medio Ambiente](../../c-runtime-library/process-and-environment-control.md)<br/>
[Constantes ambientales](../../c-runtime-library/environmental-constants.md)<br/>
[_dupenv_s_dbg, _wdupenv_s_dbg](dupenv-s-dbg-wdupenv-s-dbg.md)<br/>
[getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s, _wputenv_s](putenv-s-wputenv-s.md)<br/>
