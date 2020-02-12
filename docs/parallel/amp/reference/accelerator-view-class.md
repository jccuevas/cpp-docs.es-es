---
title: accelerator_view (Clase)
ms.date: 03/27/2019
f1_keywords:
- accelerator_view
- AMPRT/accelerator_view
- AMPRT/Concurrency::accelerator_view::accelerator_view
- AMPRT/Concurrency::accelerator_view::create_marker
- AMPRT/Concurrency::accelerator_view::flush
- AMPRT/Concurrency::accelerator_view::get_accelerator
- AMPRT/Concurrency::accelerator_view::get_is_auto_selection
- AMPRT/Concurrency::accelerator_view::get_is_debug
- AMPRT/Concurrency::accelerator_view::get_queuing_mode
- AMPRT/Concurrency::accelerator_view::get_version
- AMPRT/Concurrency::accelerator_view::wait
- AMPRT/Concurrency::accelerator_view::accelerator
- AMPRT/Concurrency::accelerator_view::is_auto_selection
- AMPRT/Concurrency::accelerator_view::is_debug
- AMPRT/Concurrency::accelerator_view::queuing_mode
- AMPRT/Concurrency::accelerator_view::version
helpviewer_keywords:
- accelerator_view class
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
ms.openlocfilehash: 8990566fb3a700d61de324f725dea3ec00006d04
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127181"
---
# <a name="accelerator_view-class"></a>accelerator_view (Clase)

Representa una abstracción del dispositivo virtual en un acelerador C++ AMP de datos en paralelo.

## <a name="syntax"></a>Sintaxis

```cpp
class accelerator_view;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor de accelerator_view](#ctor)|Inicializa una nueva instancia de la clase `accelerator_view`.|
|[~ accelerator_view destructor](#dtor)|Destruye el objeto `accelerator_view`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[create_marker](#create_marker)|Devuelve un futuro para realizar un seguimiento de la finalización de todos los comandos enviados hasta ahora a este objeto `accelerator_view`.|
|[flush](#flush)|Envía todos los comandos pendientes en cola al objeto `accelerator_view` al acelerador para su ejecución.|
|[get_accelerator](#get_accelerator)|Devuelve el objeto `accelerator` para el objeto `accelerator_view`.|
|[get_is_auto_selection](#get_is_auto_selection)|Devuelve un valor booleano que indica si el Runtime seleccionará automáticamente un acelerador adecuado cuando el objeto de `accelerator_view` se pase a una [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[get_is_debug](#get_is_debug)|Devuelve un valor booleano que indica si el objeto `accelerator_view` tiene habilitada la capa de depuración para informes de errores extensos.|
|[get_queuing_mode](#get_queuing_mode)|Devuelve el modo de puesta en cola para el objeto `accelerator_view`.|
|[get_version](#get_version)|Devuelve la versión de `accelerator_view`.|
|[currir](#wait)|Espera a que finalicen todos los comandos enviados al objeto `accelerator_view`.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator!=](#operator_neq)|Compara este objeto `accelerator_view` con otro y devuelve **false** si son iguales; de lo contrario, devuelve **true**.|
|[operator=](#operator_eq)|Copia el contenido del objeto `accelerator_view` especificado en este.|
|[operator==](#operator_eq_eq)|Compara este objeto `accelerator_view` con otro y devuelve **true** si son iguales; de lo contrario, devuelve **false**.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[métodos](#accelerator)|Obtiene el objeto `accelerator` para el objeto `accelerator_view`.|
|[is_auto_selection](#is_auto_selection)|Obtiene un valor booleano que indica si el Runtime seleccionará automáticamente un acelerador adecuado cuando el objeto de `accelerator_view` se pase a una [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[is_debug](#is_debug)|Obtiene un valor booleano que indica si el objeto `accelerator_view` tiene habilitada la capa de depuración para informes de errores extensos.|
|[queuing_mode](#queuing_mode)|Obtiene el modo de puesta en cola para el objeto `accelerator_view`.|
|[version](#version)|Obtiene la versión del acelerador.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`accelerator_view`

### <a name="remarks"></a>Observaciones

Un objeto `accelerator_view` representa una vista lógica y aislada de un acelerador. Un único dispositivo físico de proceso puede tener muchos objetos `accelerator_view` lógicos y aislados. Cada acelerador tiene un objeto de `accelerator_view` predeterminado. Se pueden crear objetos de `accelerator_view` adicionales.

Los dispositivos físicos se pueden compartir entre varios subprocesos de cliente. Los subprocesos de cliente pueden usar de forma cooperativa el mismo `accelerator_view` objeto de un acelerador, o cada cliente puede comunicarse con un dispositivo de proceso a través de un objeto de `accelerator_view` independiente para el aislamiento de otros subprocesos de cliente.

Un objeto `accelerator_view` puede tener uno de dos Estados de [enumeración queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) . Si el modo de puesta en cola es `immediate`, los comandos como `copy` y `parallel_for_each` se envían al dispositivo de acelerador correspondiente en cuanto vuelven al llamador. Si el modo de puesta en cola es `deferred`, estos comandos se ponen en cola en una cola de comandos que corresponde al objeto `accelerator_view`. Los comandos no se envían realmente al dispositivo hasta que se llama a `flush()`.

## <a name="requirements"></a>Requisitos

**Encabezado:** amprt. h

**Espacio de nombres:** Concurrency

## <a name="accelerator"></a>métodos

Obtiene el objeto de acelerador para el objeto accelerator_view.

### <a name="syntax"></a>Sintaxis

```cpp
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

## <a name="ctor"></a>accelerator_view

Inicializa una nueva instancia de la clase accelerator_view copiando un objeto `accelerator_view` existente.

### <a name="syntax"></a>Sintaxis

```cpp
accelerator_view( const accelerator_view & other );
```

### <a name="parameters"></a>Parámetros

*other*<br/>
El objeto `accelerator_view` que se va a copiar.

## <a name="create_marker"></a>create_marker

Devuelve un futuro para realizar un seguimiento de la finalización de todos los comandos enviados hasta ahora a este objeto `accelerator_view`.

### <a name="syntax"></a>Sintaxis

```cpp
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>Valor devuelto

Un futuro para realizar un seguimiento de la finalización de todos los comandos enviados hasta ahora a este objeto `accelerator_view`.

## <a name="flush"></a>flush

Envía todos los comandos pendientes en cola al objeto accelerator_view al acelerador para su ejecución.

### <a name="syntax"></a>Sintaxis

```cpp
void flush();
```

### <a name="return-value"></a>Valor devuelto

Devuelve `void`.

## <a name="get_accelerator"></a>get_accelerator

Devuelve el objeto de acelerador para el objeto accelerator_view.

### <a name="syntax"></a>Sintaxis

```cpp
accelerator get_accelerator() const;
```

### <a name="return-value"></a>Valor devuelto

Objeto de acelerador para el objeto de accelerator_view.

## <a name="get_is_auto_selection"></a>get_is_auto_selection

Devuelve un valor booleano que indica si el Runtime seleccionará automáticamente un acelerador adecuado cuando el accelerator_view se pase a una [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Sintaxis

```cpp
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si el Runtime seleccionará automáticamente un acelerador adecuado; en caso contrario, **false**.

## <a name="get_is_debug"></a>get_is_debug

Devuelve un valor booleano que indica si el objeto accelerator_view tiene habilitada la capa de depuración para informes de errores extensos.

### <a name="syntax"></a>Sintaxis

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>Valor devuelto

Valor booleano que indica si el objeto `accelerator_view` tiene habilitada la capa de depuración para informes de errores extensos.

## <a name="get_queuing_mode"></a>get_queuing_mode

Devuelve el modo de puesta en cola para el objeto accelerator_view.

### <a name="syntax"></a>Sintaxis

```cpp
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>Valor devuelto

Modo de puesta en cola para el objeto de `accelerator_view`.

## <a name="get_version"></a>get_version

Devuelve la versión de accelerator_view.

### <a name="syntax"></a>Sintaxis

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>Valor devuelto

La versión de `accelerator_view`.

## <a name="is_auto_selection"></a>is_auto_selection

Obtiene un valor booleano que indica si el Runtime seleccionará automáticamente un acelerador adecuado cuando el accelerator_view se pase a una [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Sintaxis

```cpp
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

## <a name="is_debug"></a>is_debug

Obtiene un valor booleano que indica si el objeto accelerator_view tiene habilitada la capa de depuración para informes de errores extensos.

### <a name="syntax"></a>Sintaxis

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="operator_neq"></a>operador! =

Compara este objeto accelerator_view con otro y devuelve **false** si son iguales; de lo contrario, devuelve **true**.

### <a name="syntax"></a>Sintaxis

```cpp
bool operator!= ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>Parámetros

*other*<br/>
Objeto `accelerator_view` que se va a comparar con este.

### <a name="return-value"></a>Valor devuelto

**false** si los dos objetos son iguales; en caso contrario, **true**.

## <a name="operator_eq"></a>operador =

Copia el contenido del objeto accelerator_view especificado en este.

### <a name="syntax"></a>Sintaxis

```cpp
accelerator_view & operator= ( const accelerator_view & other );
```

### <a name="parameters"></a>Parámetros

*other*<br/>
Objeto de `accelerator_view` del que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto de `accelerator_view` modificado.

## <a name="operator_eq_eq"></a>operador = =

Compara este objeto accelerator_view con otro y devuelve **true** si son iguales; de lo contrario, devuelve **false**.

### <a name="syntax"></a>Sintaxis

```cpp
bool operator== ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>Parámetros

*other*<br/>
Objeto `accelerator_view` que se va a comparar con este.

### <a name="return-value"></a>Valor devuelto

**true** si los dos objetos son iguales; en caso contrario, **false**.

## <a name="queuing_mode"></a>queuing_mode

Obtiene el modo de puesta en cola para el objeto accelerator_view.

### <a name="syntax"></a>Sintaxis

```cpp
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

## <a name="version"></a>version

Obtiene la versión de accelerator_view.

### <a name="syntax"></a>Sintaxis

```cpp
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="wait"></a>wait

Espera a que finalicen todos los comandos enviados al objeto accelerator_view.

### <a name="syntax"></a>Sintaxis

```cpp
void wait();
```

### <a name="return-value"></a>Valor devuelto

Devuelve `void`.

### <a name="remarks"></a>Observaciones

Si el [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) es `immediate`, este método vuelve inmediatamente sin bloquearse.

## <a name="dtor"></a>~ accelerator_view

Destruye el objeto de accelerator_view.

### <a name="syntax"></a>Sintaxis

```cpp
~accelerator_view();
```

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
