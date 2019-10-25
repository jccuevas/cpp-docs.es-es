---
title: _matherr
ms.date: 04/05/2018
api_name:
- _matherr
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
- _matherr
- matherr
helpviewer_keywords:
- _matherr function
- matherr function
ms.assetid: b600d66e-165a-4608-a856-8fb418d46760
ms.openlocfilehash: 340e3b8562e1f0f564810bc63cf6bd2e87ffdf63
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952756"
---
# <a name="_matherr"></a>_matherr

Trata errores matemáticos.

## <a name="syntax"></a>Sintaxis

```C
int _matherr( struct _exception * except );
```

### <a name="parameters"></a>Parámetros

*except*<br/>
Puntero a la estructura que contiene información de error.

## <a name="return-value"></a>Valor devuelto

**_matherr** devuelve 0 para indicar un error o un valor distinto de cero para indicar que la operación se ha realizado correctamente. Si **_matherr** devuelve 0, se puede mostrar un mensaje de error y **errno** se establece en un valor de error adecuado. Si **_matherr** devuelve un valor distinto de cero, no se muestra ningún mensaje de error y **errno** permanece inalterado.

Para obtener más información sobre los códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

La función **_matherr** procesa los errores generados por las funciones de punto flotante de la biblioteca matemática. Estas funciones llaman a **_matherr** cuando se detecta un error.

Para un control de errores especial, puede proporcionar una definición diferente de **_matherr**. Si usa la versión vinculada dinámicamente de la biblioteca en tiempo de ejecución de C (CRT), puede reemplazar la rutina **_matherr** predeterminada en un ejecutable de cliente con una versión definida por el usuario. Sin embargo, no puede reemplazar la rutina **_matherr** predeterminada en un cliente DLL del archivo dll de CRT.

Cuando se produce un error en una rutina matemática, se llama a **_matherr** con un puntero a una estructura de tipo **_exception** (definida en \<Math. h >) como argumento. La estructura **_exception** contiene los siguientes elementos.

```C
struct _exception
{
    int    type;   // exception type - see below
    char*  name;   // name of function where error occurred
    double arg1;   // first argument to function
    double arg2;   // second argument (if any) to function
    double retval; // value to be returned by function
};
```

El miembro de **tipo** especifica el tipo de error matemático. Es uno de los valores siguientes, definidos en \<Math. h >:

|Macro|Significado|
|-|-|
| **_DOMAIN** | Error de dominio de argumento |
| **_SING** | Singularidad de los argumentos |
| **_OVERFLOW** | Error de intervalo de desbordamiento |
| **_PLOSS** | Pérdida parcial de importancia |
| **_TLOSS** | Pérdida total de importancia |
| **_UNDERFLOW** | El resultado es demasiado pequeño para representarlo (esta condición no se admite actualmente). |

El miembro de estructura **name** es un puntero a una cadena terminada en nulo que contiene el nombre de la función que produjo el error. Los miembros de estructura **arg1** y **arg2** especifican los valores que provocaron el error Si solo se proporciona un argumento, se almacena en **arg1**.

El valor devuelto predeterminado del valor indicado es **retval**. Si cambia el valor devuelto, se debe especificar si realmente se produjo un error.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_matherr**|\<math.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_matherr.c
/* illustrates writing an error routine for math
* functions. The error function must be:
*      _matherr
*/

#include <math.h>
#include <string.h>
#include <stdio.h>

int main()
{
    /* Do several math operations that cause errors. The _matherr
     * routine handles _DOMAIN errors, but lets the system handle
     * other errors normally.
     */
    printf( "log( -2.0 ) = %e\n", log( -2.0 ) );
    printf( "log10( -5.0 ) = %e\n", log10( -5.0 ) );
    printf( "log( 0.0 ) = %e\n", log( 0.0 ) );
}

/* Handle several math errors caused by passing a negative argument
* to log or log10 (_DOMAIN errors). When this happens, _matherr
* returns the natural or base-10 logarithm of the absolute value
* of the argument and suppresses the usual error message.
*/
int _matherr( struct _exception *except )
{
    /* Handle _DOMAIN errors for log or log10. */
    if( except->type == _DOMAIN )
    {
        if( strcmp( except->name, "log" ) == 0 )
        {
            except->retval = log( -(except->arg1) );
            printf( "Special: using absolute value: %s: _DOMAIN "
                     "error\n", except->name );
            return 1;
        }
        else if( strcmp( except->name, "log10" ) == 0 )
        {
            except->retval = log10( -(except->arg1) );
            printf( "Special: using absolute value: %s: _DOMAIN "
                     "error\n", except->name );
            return 1;
        }
    }
    printf( "Normal: " );
    return 0;    /* Else use the default actions */
}
```

```Output
Special: using absolute value: log: _DOMAIN error
log( -2.0 ) = 6.931472e-01
Special: using absolute value: log10: _DOMAIN error
log10( -5.0 ) = 6.989700e-01
Normal: log( 0.0 ) = -inf
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
