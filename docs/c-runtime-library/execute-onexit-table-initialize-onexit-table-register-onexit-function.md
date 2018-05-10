---
title: _execute_onexit_table, _initialize_onexit_table, _register_onexit_function | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- _execute_onexit_table
- _initialize_onexit_table
- _register_onexit_function
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _execute_onexit_table
- process/_execute_onexit_table
- _initialize_onexit_table
- process/_initialize_onexit_table
- _register_onexit_function
- process/_register_onexit_function
dev_langs:
- C++
helpviewer_keywords:
- _execute_onexit_table function
- _initialize_onexit_table function
- _register_onexit_function function
ms.assetid: ad9e4149-d4ad-4fdf-aaaf-cf786fcb4473
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1e1f4ebf40bc242d0daf98bbc85c2ea3d1295043
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="executeonexittable-initializeonexittable-registeronexitfunction"></a>_execute_onexit_table, _initialize_onexit_table, _register_onexit_function
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
 [inout] `table`  
 Puntero a la tabla de funciones onexit.  
  
 [in] `function`  
 Puntero a una función que se agrega a la tabla de funciones onexit.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve 0. De lo contrario, devuelve un valor negativo.  
  
## <a name="remarks"></a>Comentarios  
 Estas funciones corresponden a detalles de implementación de la infraestructura que se usan para admitir el tiempo de ejecución de C y no deben llamarse directamente desde el código. El tiempo de ejecución de C usa una *tabla de funciones onexit* para representar la secuencia de las funciones registradas por llamadas a `atexit`, `at_quick_exit` y `_onexit`. La estructura de datos de la tabla de funciones onexit es un detalle de implementación opaco del tiempo de ejecución de C; puede que el orden y el significado de sus miembros de datos cambien. No deben comprobarse mediante código externo.  
  
 La función `_initialize_onexit_table` inicializa la tabla de funciones onexit a su valor inicial.  Esta función debe llamarse antes de pasar la tabla de funciones onexit a `_register_onexit_function` o `_execute_onexit_table`.  
  
 La función `_register_onexit_function` anexa una función al final de la tabla de funciones onexit.  
  
 La función `_execute_onexit_table` ejecuta todas las funciones de la tabla de funciones onexit, borra la tabla y luego vuelve. Después de una llamada a `_execute_onexit_table`, la tabla se encuentra en un estado no válido; debe reinicializarse mediante una llamada a `_initialize_onexit_table` antes de usarla de nuevo.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_initialize_onexit_table function`, `_register_onexit_function`, `_execute_onexit_table`|C, C++: \<process.h>|  
  
 Las funciones `_initialize_onexit_table`, `_register_onexit_function` y `_execute_onexit_table` son específicas de Microsoft. Para obtener información sobre la compatibilidad, consulte [Compatibilidad](../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [atexit](../c-runtime-library/reference/atexit.md)   
 [exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)