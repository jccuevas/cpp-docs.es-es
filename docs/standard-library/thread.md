---
title: '&lt;thread&gt;'
ms.date: 11/04/2016
f1_keywords:
- <thread>
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
ms.openlocfilehash: 7053402dfb566f10c7be4c0eebaef40f3d371f43
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460072"
---
# <a name="ltthreadgt"></a>&lt;thread&gt;

Incluya el subproceso \<de encabezado estándar > para definir el subproceso de clase y varias funciones auxiliares.

## <a name="syntax"></a>Sintaxis

```cpp
#include <thread>
```

## <a name="remarks"></a>Comentarios

> [!NOTE]
> En el código compilado mediante **/CLR**, este encabezado está bloqueado.

La `__STDCPP_THREADS__` macro se define como un valor distinto de cero para indicar que este encabezado admite los subprocesos.

## <a name="members"></a>Miembros

### <a name="public-classes"></a>Clases públicas

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[thread (Clase)](../standard-library/thread-class.md)|Define un objeto que se utiliza para observar y administrar un subproceso de ejecución en una aplicación.|

### <a name="public-structures"></a>Estructuras públicas

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[hash (Estructura, biblioteca estándar de C++)](../standard-library/hash-structure-stl.md)|Define una función miembro que devuelve un valor que está determinado de forma exclusiva por `thread::id`un. La función miembro define una función [hash](../standard-library/hash-class.md) que es adecuada para asignar valores de tipo `thread::id` a una distribución de valores de índice.|

### <a name="public-functions"></a>Funciones públicas

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[get_id](../standard-library/thread-functions.md#get_id)|Identifica de forma única el subproceso de ejecución actual.|
|[sleep_for](../standard-library/thread-functions.md#sleep_for)|Bloquea el subproceso de llamada.|
|[sleep_until](../standard-library/thread-functions.md#sleep_until)|Bloquea el subproceso de llamada al menos hasta la hora especificada.|
|[swap](../standard-library/thread-functions.md#swap)|Intercambia los Estados de dos  objetos de subproceso.|
|[yield](../standard-library/thread-functions.md#yield)|Indica al sistema operativo que ejecute otros subprocesos, incluso si el subproceso actual seguiría ejecutándose en condiciones normales.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[Operator > = (operador)](../standard-library/thread-operators.md#op_gt_eq)|Determina si un objeto `thread::id` es mayor o igual que otro objeto.|
|[operador Operator >](../standard-library/thread-operators.md#op_gt)|Determina si un objeto `thread::id` es mayor que otro objeto.|
|[Operator < = (operador)](../standard-library/thread-operators.md#op_lt_eq)|Determina si un objeto `thread::id` es menor o igual que otro objeto.|
|[operador Operator <](../standard-library/thread-operators.md#op_lt)|Determina si un objeto `thread::id` es menor que otro objeto.|
|[Operator! = (operador)](../standard-library/thread-operators.md#op_neq)|Compara dos objetos `thread::id` para determinar si no son iguales.|
|[Operator = = (operador)](../standard-library/thread-operators.md#op_eq_eq)|Compara dos objetos `thread::id` para determinar si son iguales.|
|[Operator < operador de <](../standard-library/thread-operators.md#op_lt_lt)|Inserta una representación de texto de un objeto `thread::id` en una secuencia.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
