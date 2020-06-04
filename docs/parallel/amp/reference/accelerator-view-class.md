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
ms.openlocfilehash: f3be8cc3ab9a0f36027cc38c88f026570d1fdb55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370888"
---
# <a name="accelerator_view-class"></a>accelerator_view (Clase)

Representa una abstracción del dispositivo virtual en un acelerador C++ AMP de datos en paralelo.

## <a name="syntax"></a>Sintaxis

```cpp
class accelerator_view;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor accelerator_view](#ctor)|Inicializa una nueva instancia de la clase `accelerator_view`.|
|[Destructor de accelerator_view](#dtor)|Destruye el objeto `accelerator_view`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[create_marker](#create_marker)|Devuelve un futuro para realizar un seguimiento de `accelerator_view` la finalización de todos los comandos enviados hasta ahora a este objeto.|
|[rubor](#flush)|Envía todos los comandos `accelerator_view` pendientes en cola al objeto al acelerador para su ejecución.|
|[get_accelerator](#get_accelerator)|Devuelve el objeto `accelerator` para el objeto `accelerator_view`.|
|[get_is_auto_selection](#get_is_auto_selection)|Devuelve un valor booleano que indica si el tiempo `accelerator_view` de ejecución seleccionará automáticamente un acelerador adecuado cuando el objeto se pasa a un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[get_is_debug](#get_is_debug)|Devuelve un valor booleano `accelerator_view` que indica si el objeto tiene la capa DEBUG habilitada para informes de errores extensos.|
|[get_queuing_mode](#get_queuing_mode)|Devuelve el modo de `accelerator_view` cola para el objeto.|
|[get_version](#get_version)|Devuelve la versión del `accelerator_view`archivo .|
|[Esperar](#wait)|Espera a que finalicen `accelerator_view` todos los comandos enviados al objeto.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[¡Operador!](#operator_neq)|Compara este `accelerator_view` objeto con otro y devuelve **false** si son iguales; de lo contrario, devuelve **true**.|
|[operador](#operator_eq)|Copia el contenido del `accelerator_view` objeto especificado en éste.|
|[operadora](#operator_eq_eq)|Compara este `accelerator_view` objeto con otro y devuelve **true** si son iguales; de lo contrario, devuelve **false**.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Acelerador](#accelerator)|Obtiene el objeto `accelerator` para el objeto `accelerator_view`.|
|[is_auto_selection](#is_auto_selection)|Obtiene un valor booleano que indica si el tiempo `accelerator_view` de ejecución seleccionará automáticamente un acelerador adecuado cuando el objeto se pasa a un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[is_debug](#is_debug)|Obtiene un valor booleano que `accelerator_view` indica si el objeto tiene la capa DEBUG habilitada para informes de errores extensos.|
|[queuing_mode](#queuing_mode)|Obtiene el modo de cola `accelerator_view` para el objeto.|
|[version](#version)|Obtiene la versión del acelerador.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`accelerator_view`

### <a name="remarks"></a>Observaciones

Un `accelerator_view` objeto representa una vista lógica y aislada de un acelerador. Un único dispositivo de proceso físico `accelerator_view` puede tener muchos objetos lógicos y aislados. Cada acelerador tiene `accelerator_view` un objeto predeterminado. Se `accelerator_view` pueden crear objetos adicionales.

Los dispositivos físicos se pueden compartir entre muchos subprocesos de cliente. Los subprocesos de cliente `accelerator_view` pueden usar de forma cooperativa el mismo objeto `accelerator_view` de un acelerador, o cada cliente puede comunicarse con un dispositivo de proceso a través de un objeto independiente para el aislamiento de otros subprocesos de cliente.

Un `accelerator_view` objeto puede tener uno de los dos queuing_mode los estados [de enumeración.](concurrency-namespace-enums-amp.md#queuing_mode) Si el modo de `immediate`cola `copy` es `parallel_for_each` , comandos como y se envían al dispositivo acelerador correspondiente tan pronto como vuelvan al autor de la llamada. Si el modo de `deferred`cola es , estos comandos se ponen `accelerator_view` en cola en una cola de mandatos que corresponde al objeto. Los comandos no se `flush()` envían realmente al dispositivo hasta que se llama.

## <a name="requirements"></a>Requisitos

**Encabezado:** amprt.h

**Espacio de nombres:** Concurrencia

## <a name="accelerator"></a><a name="accelerator"></a>Acelerador

Obtiene el objeto acelerador para el objeto accelerator_view.

### <a name="syntax"></a>Sintaxis

```cpp
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

## <a name="accelerator_view"></a><a name="ctor"></a>accelerator_view

Inicializa una nueva instancia de la clase `accelerator_view` accelerator_view copiando un objeto existente.

### <a name="syntax"></a>Sintaxis

```cpp
accelerator_view( const accelerator_view & other );
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
El objeto `accelerator_view` que se va a copiar.

## <a name="create_marker"></a><a name="create_marker"></a>create_marker

Devuelve un futuro para realizar un seguimiento de `accelerator_view` la finalización de todos los comandos enviados hasta ahora a este objeto.

### <a name="syntax"></a>Sintaxis

```cpp
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>Valor devuelto

Un futuro para realizar un seguimiento de `accelerator_view` la finalización de todos los comandos enviados hasta ahora a este objeto.

## <a name="flush"></a>flush

Envía todos los comandos pendientes en cola al objeto accelerator_view al acelerador para su ejecución.

### <a name="syntax"></a>Sintaxis

```cpp
void flush();
```

### <a name="return-value"></a>Valor devuelto

Devuelve `void`.

## <a name="get_accelerator"></a><a name="get_accelerator"></a>get_accelerator

Devuelve el objeto acelerador para el objeto accelerator_view.

### <a name="syntax"></a>Sintaxis

```cpp
accelerator get_accelerator() const;
```

### <a name="return-value"></a>Valor devuelto

El objeto acelerador para el objeto accelerator_view.

## <a name="get_is_auto_selection"></a><a name="get_is_auto_selection"></a>get_is_auto_selection

Devuelve un valor booleano que indica si el tiempo de ejecución seleccionará automáticamente un acelerador adecuado cuando el accelerator_view se pasa a un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Sintaxis

```cpp
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si el tiempo de ejecución seleccionará automáticamente un acelerador adecuado; de lo contrario, **false**.

## <a name="get_is_debug"></a><a name="get_is_debug"></a>get_is_debug

Devuelve un valor booleano que indica si el objeto accelerator_view tiene habilitada la capa DEBUG para informes de errores extensos.

### <a name="syntax"></a>Sintaxis

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>Valor devuelto

Valor booleano que indica `accelerator_view` si el objeto tiene habilitada la capa DEBUG para informes de errores extensos.

## <a name="get_queuing_mode"></a><a name="get_queuing_mode"></a>get_queuing_mode

Devuelve el modo de cola para el objeto accelerator_view.

### <a name="syntax"></a>Sintaxis

```cpp
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>Valor devuelto

El modo de cola `accelerator_view` para el objeto.

## <a name="get_version"></a><a name="get_version"></a>get_version

Devuelve la versión del accelerator_view.

### <a name="syntax"></a>Sintaxis

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>Valor devuelto

La versión de `accelerator_view`.

## <a name="is_auto_selection"></a><a name="is_auto_selection"></a>is_auto_selection

Obtiene un valor booleano que indica si el tiempo de ejecución seleccionará automáticamente un acelerador adecuado cuando el accelerator_view se pasa a un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Sintaxis

```cpp
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

## <a name="is_debug"></a><a name="is_debug"></a>is_debug

Obtiene un valor booleano que indica si el objeto accelerator_view tiene la capa DEBUG habilitada para informes de errores extensos.

### <a name="syntax"></a>Sintaxis

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="operator"></a><a name="operator_neq"></a>¡Operador!

Compara este objeto accelerator_view con otro y devuelve **false** si son iguales; de lo contrario, devuelve **true**.

### <a name="syntax"></a>Sintaxis

```cpp
bool operator!= ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
El `accelerator_view` objeto que se va a comparar con éste.

### <a name="return-value"></a>Valor devuelto

**false** si los dos objetos son iguales; de lo contrario, **true**.

## <a name="operator"></a><a name="operator_eq"></a>operador

Copia el contenido del objeto accelerator_view especificado en éste.

### <a name="syntax"></a>Sintaxis

```cpp
accelerator_view & operator= ( const accelerator_view & other );
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
Objeto `accelerator_view` desde el que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Una referencia al `accelerator_view` objeto modificado.

## <a name="operator"></a><a name="operator_eq_eq"></a>operadora

Compara este objeto accelerator_view con otro y devuelve **true** si son iguales; de lo contrario, devuelve **false**.

### <a name="syntax"></a>Sintaxis

```cpp
bool operator== ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
El `accelerator_view` objeto que se va a comparar con éste.

### <a name="return-value"></a>Valor devuelto

**true** si los dos objetos son iguales; de lo contrario, **false**.

## <a name="queuing_mode"></a><a name="queuing_mode"></a>queuing_mode

Obtiene el modo de cola para el objeto accelerator_view.

### <a name="syntax"></a>Sintaxis

```cpp
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

## <a name="version"></a>version

Obtiene la versión del accelerator_view.

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

Si [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) el `immediate`queuing_mode es , este método devuelve inmediatamente sin bloquear.

## <a name="accelerator_view"></a><a name="dtor"></a>Accelerator_view

Destruye el objeto accelerator_view.

### <a name="syntax"></a>Sintaxis

```cpp
~accelerator_view();
```

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
