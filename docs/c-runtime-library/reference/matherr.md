---
title: _matherr | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _matherr
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
apitype: DLLExport
f1_keywords:
- _matherr
- matherr
dev_langs:
- C++
helpviewer_keywords:
- _matherr function
- matherr function
ms.assetid: b600d66e-165a-4608-a856-8fb418d46760
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f8cba1887fe806c3a6cfa795437d3d60ed7f31e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402330"
---
# <a name="matherr"></a>_matherr

Trata errores matemáticos.

## <a name="syntax"></a>Sintaxis

```C
int _matherr( struct _exception * except );
```

### <a name="parameters"></a>Parámetros

*except*<br/>
Puntero a la estructura que contiene información de error.

## <a name="return-value"></a>Valor devuelto

**_matherr** devuelve 0 para indicar un error o un valor distinto de cero para indicar una operación correcta. Si **_matherr** devuelve 0, un mensaje de error se puede mostrar y **errno** se establece en un valor de error adecuado. Si **_matherr** devuelve un valor distinto de cero, no hay ningún mensaje de error se muestra y **errno** permanece sin cambios.

Para obtener más información sobre los códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_matherr** función procesa los errores generados por las funciones de punto flotante de la biblioteca matemática. Llamar estas funciones **_matherr** cuando se detecta un error.

Para el control de error especial, puede proporcionar una definición diferente de **_matherr**. Si utiliza la versión vinculada dinámicamente de la biblioteca de tiempo de ejecución de C (CRT), puede reemplazar el valor predeterminado **_matherr** rutinarias en un ejecutable con una versión definido por el usuario del cliente. Sin embargo, no se puede reemplazar el valor predeterminado **_matherr** rutinarias en un cliente DLL de la DLL de CRT.

Cuando se produce un error en una rutina de matemáticas, **_matherr** se llama con un puntero a un **_exception** estructura de tipo (definido en \<math.h >) como argumento. La estructura **_exception** contiene los siguientes elementos.

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

El **tipo** miembro especifica el tipo de error matemático. Es uno de los valores siguientes, definidos en \<math.h >:

|Macro|Significado|
|-|-|
**_DOMAIN**|Error de dominio de argumento
**_SING**|Singularidad de argumento
**_OVERFLOW**|Error de intervalo de desbordamiento
**_PLOSS**|Pérdida parcial de importancia
**_TLOSS**|Pérdida total de significado
**_UNDERFLOW**|El resultado es demasiado pequeño para representarlo (esta condición no se admite actualmente).

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
