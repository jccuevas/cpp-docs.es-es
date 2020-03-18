---
title: event (clase)
ms.date: 11/04/2016
f1_keywords:
- CONCRT/concurrency::event
- CONCRT/concurrency::event::reset
- CONCRT/concurrency::event::set
- CONCRT/concurrency::event::wait
- CONCRT/concurrency::event::wait_for_multiple
- CONCRT/concurrency::event::timeout_infinite
helpviewer_keywords:
- event class
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
ms.openlocfilehash: 3d645cc09c61402059e9a86679c10ee703ee8031
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443734"
---
# <a name="event-class"></a>event (clase)

Un evento de reinicio manual que es explícitamente consciente del runtime de simultaneidad.

## <a name="syntax"></a>Sintaxis

```cpp
class event;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[~ (destructor de eventos)](#dtor)|Destruye un evento.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[reset](#reset)|Restablece el evento a un estado no señalado.|
|[set](#set)|Señala el evento.|
|[currir](#wait)|Espera a que se señale el evento.|
|[wait_for_multiple](#wait_for_multiple)|Espera a que se señalen varios eventos.|

### <a name="public-constants"></a>Constantes públicas

|Nombre|Descripción|
|----------|-----------------|
|[timeout_infinite](#timeout_infinite)|Valor que indica que una espera nunca debe agotar el tiempo de espera.|

## <a name="remarks"></a>Observaciones

Para obtener más información, vea [Synchronization Data Structures](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`event`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

**Espacio de nombres:** simultaneidad

## <a name="ctor"></a>ceso

Construye un nuevo evento.

```cpp
_CRTIMP event();
```

### <a name="remarks"></a>Observaciones

## <a name="dtor"></a>evento ~

Destruye un evento.

```cpp
~event();
```

### <a name="remarks"></a>Observaciones

Se espera que no haya ningún subproceso esperando en el evento cuando el destructor se ejecuta. Permitir que el evento se destruya con subprocesos que todavía esperan da como resultado un comportamiento no definido.

## <a name="reset"></a>determinado

Restablece el evento a un estado no señalado.

```cpp
void reset();
```

## <a name="set"></a>conjunto

Señala el evento.

```cpp
void set();
```

### <a name="remarks"></a>Observaciones

Señalar el evento puede producir un número arbitrario de contextos que esperan en el evento para que se convierta en ejecutable.

## <a name="timeout_infinite"></a>timeout_infinite

Valor que indica que una espera nunca debe agotar el tiempo de espera.

```cpp
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```

## <a name="wait"></a>currir

Espera a que se señale el evento.

```cpp
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parámetros

*_Timeout*<br/>
Indica el número de milisegundos antes de que se agote el tiempo de espera. El valor `COOPERATIVE_TIMEOUT_INFINITE` significa que no hay tiempo de espera.

### <a name="return-value"></a>Valor devuelto

Si se satisfizo la espera, se devuelve el valor `0`; de lo contrario, se devuelve el valor `COOPERATIVE_WAIT_TIMEOUT` para indicar que el tiempo de la espera se agota sin haber señalado el evento.

> [!IMPORTANT]
> En una aplicación Plataforma universal de Windows (UWP), no llame a `wait` en el subproceso de ASTA porque esta llamada puede bloquear el subproceso actual y puede hacer que la aplicación deje de responder.

## <a name="wait_for_multiple"></a>wait_for_multiple

Espera a que se señalen varios eventos.

```cpp
static size_t __cdecl wait_for_multiple(
    _In_reads_(count) event** _PPEvents,
    size_t count,
    bool _FWaitAll,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parámetros

*_PPEvents*<br/>
Matriz de eventos en la que se va a esperar. El número de eventos dentro de la matriz viene indicado por el parámetro `count`.

*count*<br/>
El número de eventos dentro de la matriz proporcionado por el parámetro `_PPEvents`.

*_FWaitAll*<br/>
Si se establece en el valor **true**, el parámetro especifica que todos los eventos de la matriz proporcionada en el parámetro `_PPEvents` se deben señalizar para satisfacer la espera. Si se establece en el valor **false**, especifica que cualquier evento incluido en la matriz proporcionada en el parámetro `_PPEvents` que se va a señalar satisfará la espera.

*_Timeout*<br/>
Indica el número de milisegundos antes de que se agote el tiempo de espera. El valor `COOPERATIVE_TIMEOUT_INFINITE` significa que no hay tiempo de espera.

### <a name="return-value"></a>Valor devuelto

Si se satisfizo la espera, el índice de la matriz proporcionada en el parámetro `_PPEvents` que satisfizo la condición de espera; de lo contrario, el valor `COOPERATIVE_WAIT_TIMEOUT` para indicar que el tiempo de la espera se agota sin satisfacer la condición.

### <a name="remarks"></a>Observaciones

Si el parámetro `_FWaitAll` está establecido en el valor `true` para indicar que todos los eventos se deben señalar para satisfacer la espera, el índice que devuelve la función no tiene ninguna importancia especial aparte del hecho de que no es el valor `COOPERATIVE_WAIT_TIMEOUT`.

> [!IMPORTANT]
> En una aplicación Plataforma universal de Windows (UWP), no llame a `wait_for_multiple` en el subproceso de ASTA porque esta llamada puede bloquear el subproceso actual y puede hacer que la aplicación deje de responder.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
