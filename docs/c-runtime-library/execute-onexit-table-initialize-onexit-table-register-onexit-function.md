---
title: _execute_onexit_table, _initialize_onexit_table, _register_onexit_function
ms.date: 4/2/2020
api_name:
- _execute_onexit_table
- _initialize_onexit_table
- _register_onexit_function
- _o__execute_onexit_table
- _o__initialize_onexit_table
- _o__register_onexit_function
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _execute_onexit_table
- process/_execute_onexit_table
- _initialize_onexit_table
- process/_initialize_onexit_table
- _register_onexit_function
- process/_register_onexit_function
helpviewer_keywords:
- _execute_onexit_table function
- _initialize_onexit_table function
- _register_onexit_function function
ms.assetid: ad9e4149-d4ad-4fdf-aaaf-cf786fcb4473
ms.openlocfilehash: 051961f049109b4fa6a2881e442e621036cb279c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913836"
---
# <a name="_execute_onexit_table-_initialize_onexit_table-_register_onexit_function"></a>_execute_onexit_table, _initialize_onexit_table, _register_onexit_function

Administra las rutinas que se llaman a la hora de salida.

## <a name="syntax"></a>Sintaxis

```
int _initialize_onexit_table(
    _onexit_table_t* table
    );

int _register_onexit_function(
    _onexit_table_t* table,
    _onexit_t        function
    );

int _execute_onexit_table(
    _onexit_table_t* table
    );
```

#### <a name="parameters"></a>Parámetros

*table*<br/>
[in, out] Puntero a la tabla de funciones onexit.

*function*<br/>
[in] Puntero a una función que se agrega a la tabla de funciones onexit.

## <a name="return-value"></a>Valor devuelto

Si la operación se realiza correctamente, devuelve 0. De lo contrario, devuelve un valor negativo.

## <a name="remarks"></a>Observaciones

Estas funciones corresponden a detalles de implementación de la infraestructura que se usan para admitir el tiempo de ejecución de C y no deben llamarse directamente desde el código. El tiempo de ejecución de C usa una tabla de funciones *OnExit* para representar la secuencia de funciones registradas `at_quick_exit`por las `_onexit`llamadas a `atexit`, y. La estructura de datos de la tabla de funciones onexit es un detalle de implementación opaco del tiempo de ejecución de C; puede que el orden y el significado de sus miembros de datos cambien. No deben comprobarse mediante código externo.

La función `_initialize_onexit_table` inicializa la tabla de funciones onexit a su valor inicial.  Esta función debe llamarse antes de pasar la tabla de funciones onexit a `_register_onexit_function` o `_execute_onexit_table`.

La función `_register_onexit_function` anexa una función al final de la tabla de funciones onexit.

La función `_execute_onexit_table` ejecuta todas las funciones de la tabla de funciones onexit, borra la tabla y luego vuelve. Después de una llamada a `_execute_onexit_table`, la tabla se encuentra en un estado no válido; debe reinicializarse mediante una llamada a `_initialize_onexit_table` antes de usarla de nuevo.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`_initialize_onexit_table function`, `_register_onexit_function`, `_execute_onexit_table`|C, C++: \<process.h>|

Las `_initialize_onexit_table`funciones `_register_onexit_function`, y `_execute_onexit_table` son específicas de Microsoft. Para obtener información sobre la compatibilidad, consulte [Compatibilidad](../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[atexit](../c-runtime-library/reference/atexit.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)
