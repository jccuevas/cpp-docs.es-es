---
title: future (Clase)
ms.date: 11/04/2016
f1_keywords:
- future/std::future
- future/std::future::future
- future/std::future::get
- future/std::future::share
- future/std::future::valid
- future/std::future::wait
- future/std::future::wait_for
- future/std::future::wait_until
ms.assetid: 495e82c3-5341-4e37-87dd-b40107fbdfb6
helpviewer_keywords:
- std::future [C++]
- std::future [C++], future
- std::future [C++], get
- std::future [C++], share
- std::future [C++], valid
- std::future [C++], wait
- std::future [C++], wait_for
- std::future [C++], wait_until
ms.openlocfilehash: e71c750ddeb198faa3ae9c5960b2668c376241ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370702"
---
# <a name="future-class"></a>future (Clase)

Describe un *objeto de devolución asincrónico*.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
class future;
```

## <a name="remarks"></a>Observaciones

Cada *proveedor asincrónico* estándar devuelve un objeto cuyo tipo es una creación de instancia de esta plantilla. Un objeto `future` proporciona el único acceso al proveedor asincrónico con el que está asociado. Si necesita varios objetos de devolución asincrónicos que están asociados con el mismo proveedor asincrónico, copie el objeto `future` en un objeto [shared_future](../standard-library/shared-future-class.md).

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Futuro](#future)|Construye un objeto `future`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[get](#get)|Recupera el resultado almacenado en el estado asincrónico asociado.|
|[compartir](#share)|Convierte el objeto en un `shared_future`.|
|[Válido](#valid)|Especifica si el objeto no está vacío.|
|[Esperar](#wait)|Bloquea el subproceso actual hasta que el estado asincrónico asociado esté listo.|
|[wait_for](#wait_for)|Se bloquea hasta que el estado asincrónico asociado está listo, o bien hasta que el tiempo especificado haya transcurrido.|
|[wait_until](#wait_until)|Se bloquea hasta que el estado asincrónico asociado está listo o hasta un punto determinado en el tiempo.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[future::operator=](#op_eq)|Transfiere el estado asincrónico asociado de un objeto especificado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<futuro>

**Espacio de nombres:** std

## <a name="futurefuture-constructor"></a><a name="future"></a>futuro::futuro Constructor

Construye un objeto `future`.

```cpp
future() noexcept;
future(future&& Other) noexcept;
```

### <a name="parameters"></a>Parámetros

*Otro*\
Objeto `future` .

### <a name="remarks"></a>Observaciones

El primer constructor crea un objeto `future` que no tiene ningún estado asincrónico asociado.

El segundo constructor `future` construye un objeto y transfiere el estado asincrónico asociado de *Other*. *Otros* ya no tienen un estado asincrónico asociado.

## <a name="futureget"></a><a name="get"></a>futuro::get

Recupera el resultado almacenado en el estado asincrónico asociado.

```cpp
Ty get();
```

### <a name="return-value"></a>Valor devuelto

Si el resultado es una excepción, el método la reinicia. De lo contrario, se devuelve el resultado.

### <a name="remarks"></a>Observaciones

Antes de recuperar el resultado, este método bloquea el subproceso actual hasta que el estado asincrónico asociado esté listo.

Para la especialización parcial `future<Ty&>`, el valor almacenado es realmente una referencia al objeto que se ha pasado al proveedor asincrónico como el valor devuelto.

Dado que no existe ningún `future<void>`valor almacenado para la especialización , el método devuelve **void**.

En otras especializaciones, el método mueve su valor devuelto del valor almacenado. Por tanto, llame a este método solo una vez.

## <a name="futureoperator"></a><a name="op_eq"></a>futuro::operador ?

Transfiere un estado asincrónico asociado de un objeto especificado.

```cpp
future& operator=(future&& Right) noexcept;
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Objeto `future` .

### <a name="return-value"></a>Valor devuelto

`*this`

### <a name="remarks"></a>Observaciones

Después de la transferencia, *Right* ya no tiene un estado asincrónico asociado.

## <a name="futureshare"></a><a name="share"></a>future::share

Convierte el objeto en un objeto [shared_future](../standard-library/shared-future-class.md).

```cpp
shared_future<Ty> share();
```

### <a name="return-value"></a>Valor devuelto

`shared_future(move(*this))`

## <a name="futurevalid"></a><a name="valid"></a>futuro::válido

Especifica si el objeto tiene un estado asincrónico asociado.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Valor devuelto

**true** si el objeto tiene un estado asincrónico asociado; de lo contrario, **false**.

## <a name="futurewait"></a><a name="wait"></a>futuro::espera

Bloquea el subproceso actual hasta que el estado asincrónico asociado esté *listo*.

```cpp
void wait() const;
```

### <a name="remarks"></a>Observaciones

Un estado asincrónico asociado solo está *listo* si su proveedor asincrónico ha almacenado un valor devuelto o ha almacenado una excepción.

## <a name="futurewait_for"></a><a name="wait_for"></a>futuro::wait_for

Bloquea el subproceso actual hasta que el estado asincrónico asociado esté *listo* o hasta que haya transcurrido un tiempo especificado.

```cpp
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parámetros

*Rel_time*\
Un objeto [chrono::duration](../standard-library/duration-class.md) que especifica un intervalo de tiempo máximo que el subproceso bloquea.

### <a name="return-value"></a>Valor devuelto

Un [future_status](../standard-library/future-enums.md#future_status) que indica el motivo que se va a devolver.

### <a name="remarks"></a>Observaciones

Un estado asincrónico asociado está listo solo si su proveedor asincrónico ha almacenado un valor devuelto o ha almacenado una excepción.

## <a name="futurewait_until"></a><a name="wait_until"></a>futuro::wait_until

Bloquea el subproceso actual hasta que el estado asincrónico asociado esté *listo* o hasta después de un punto de tiempo especificado.

```cpp
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parámetros

*Abs_time*\
Un objeto [chrono::time_point](../standard-library/time-point-class.md) que especifica un tiempo después del cual se puede desbloquear el subproceso.

### <a name="return-value"></a>Valor devuelto

Un [future_status](../standard-library/future-enums.md#future_status) que indica el motivo que se va a devolver.

### <a name="remarks"></a>Observaciones

Un estado asincrónico asociado solo está *listo* si su proveedor asincrónico ha almacenado un valor devuelto o ha almacenado una excepción.

## <a name="see-also"></a>Consulte también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<>futuro](../standard-library/future.md)
