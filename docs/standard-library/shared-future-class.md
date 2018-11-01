---
title: shared_future (Clase)
ms.date: 11/04/2016
f1_keywords:
- future/std::shared_future
- future/std::shared_future::shared_future
- future/std::shared_future::get
- future/std::shared_future::valid
- future/std::shared_future::wait
- future/std::shared_future::wait_for
- future/std::shared_future::wait_until
ms.assetid: 454ebedd-f42b-405f-99a5-a25cc9ad7c90
helpviewer_keywords:
- std::shared_future [C++]
- std::shared_future [C++], shared_future
- std::shared_future [C++], get
- std::shared_future [C++], valid
- std::shared_future [C++], wait
- std::shared_future [C++], wait_for
- std::shared_future [C++], wait_until
ms.openlocfilehash: 2280c17c4ce58fe06365c107ad26d646c7ae2d72
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575635"
---
# <a name="sharedfuture-class"></a>shared_future (Clase)

Describe un *objeto de devolución asincrónico*. Al contrario que un objeto [future](../standard-library/future-class.md), un *proveedor asincrónico* se puede asociar a cualquier número de objetos `shared_future`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
class shared_future;
```

## <a name="remarks"></a>Comentarios

No llame a ningún método distinto de `valid`, `operator=` y el destructor de un objeto `shared_future` que esté *vacío*.

Los objetos `shared_future` no están sincronizados. Llamar a métodos en el mismo objeto desde varios subprocesos, presenta una anticipación de datos que tiene resultados impredecibles.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[shared_future](#shared_future)|Construye un objeto `shared_future`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[get](#get)|Recupera el resultado almacenado en el *estado asincrónico asociado*.|
|[valid](#valid)|Especifica si el objeto no está vacío.|
|[Espere](#wait)|Bloquea el subproceso actual hasta que el estado asincrónico asociado esté listo.|
|[wait_for](#wait_for)|Se bloquea hasta que el estado asincrónico asociado está listo, o bien hasta que el tiempo especificado haya transcurrido.|
|[wait_until](#wait_until)|Se bloquea hasta que el estado asincrónico asociado está listo o hasta un punto determinado en el tiempo.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[shared_future::operator=](#op_eq)|Asigna un nuevo estado asincrónico asociado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<futura >

**Espacio de nombres:** std

## <a name="get"></a>  shared_future::Get

Recupera el resultado almacenado en el *estado asincrónico asociado*.

```cpp
const Ty& get() const;

Ty& get() const;

void get() const;
```

### <a name="remarks"></a>Comentarios

Si el resultado es una excepción, el método la reinicia. De lo contrario, se devuelve el resultado.

Antes de recuperar el resultado, este método bloquea el subproceso actual hasta que el estado asincrónico asociado esté listo.

Para la especialización parcial `shared_future<Ty&>`, el valor almacenado es realmente una referencia al objeto que se pasó al *proveedor asincrónico* como el valor devuelto.

Dado que no existe ningún valor almacenado para la especialización `shared_future<void>`, el método devuelve **void**.

## <a name="op_eq"></a>  shared_future::operator=

Transfiere un *estado asincrónico asociado* de un objeto especificado.

```cpp
shared_future& operator=(shared_future&& Right) noexcept;
shared_future& operator=(const shared_future& Right);
```

### <a name="parameters"></a>Parámetros

*Derecha*<br/>
Un objeto `shared_future`.

### <a name="return-value"></a>Valor devuelto

`*this`

### <a name="remarks"></a>Comentarios

Para el primer operador, *derecha* ya no tiene un estado asincrónico asociado después de la operación.

Para el segundo método, *derecha* mantiene su estado asincrónico asociado.

## <a name="shared_future"></a>  shared_future::shared_future (Constructor)

Construye un objeto `shared_future`.

```cpp
shared_future() noexcept;
shared_future(future<Ty>&& Right) noexcept;
shared_future(shared_future&& Right) noexcept;
shared_future(const shared_future& Right);
```

### <a name="parameters"></a>Parámetros

*Derecha*<br/>
Un objeto [future](../standard-library/future-class.md) o `shared_future`.

### <a name="remarks"></a>Comentarios

El primer constructor crea un objeto `shared_future` que no tiene ningún *estado asincrónico asociado*.

Los constructores segundo y terceros crean un `shared_future` de objetos y transferir el estado asincrónico asociado de *derecha*. *Derecha* ya no tiene un estado asincrónico asociado.

El cuarto constructor crea un `shared_future` objeto que tiene el mismo estado asincrónico asociado que *derecha*.

## <a name="valid"></a>  shared_future::Valid

Especifica si el objeto tiene un *estado asincrónico asociado*.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Valor devuelto

**True** si el objeto tiene un estado asincrónico asociado; en caso contrario, **false**.

## <a name="wait"></a>  shared_future::wait

Bloquea el subproceso actual hasta que el *estado asincrónico asociado* esté *listo*.

```cpp
void wait() const;
```

### <a name="remarks"></a>Comentarios

Un estado asincrónico asociado está listo solo si su proveedor asincrónico ha almacenado un valor devuelto o ha almacenado una excepción.

## <a name="wait_for"></a>  shared_future::wait_for

Bloquea el subproceso actual hasta que el estado asincrónico asociado esté *listo* o hasta que haya transcurrido un tiempo especificado.

```cpp
template <class Rep, class Period>
future_status wait_for(
    const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parámetros

*Rel_time*<br/>
Un objeto [chrono::duration](../standard-library/duration-class.md) que especifica un intervalo de tiempo máximo que el subproceso bloquea.

### <a name="return-value"></a>Valor devuelto

Un [future_status](../standard-library/future-enums.md#future_status) que indica el motivo que se va a devolver.

### <a name="remarks"></a>Comentarios

Un estado asincrónico asociado está *listo* únicamente si su proveedor asincrónico ha almacenado un valor devuelto o una excepción.

## <a name="wait_until"></a>  shared_future::wait_until

Bloquea el subproceso actual hasta que el estado asincrónico asociado esté *listo* o hasta después de un punto de tiempo especificado.

```cpp
template <class Clock, class Duration>
future_status wait_until(
    const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parámetros

*Abs_time*<br/>
Un objeto [chrono::time_point](../standard-library/time-point-class.md) que especifica un tiempo después del cual se puede desbloquear el subproceso.

### <a name="return-value"></a>Valor devuelto

Un [future_status](../standard-library/future-enums.md#future_status) que indica el motivo que se va a devolver.

### <a name="remarks"></a>Comentarios

Un estado asincrónico asociado está listo solo si su proveedor asincrónico ha almacenado un valor devuelto o ha almacenado una excepción.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<future>](../standard-library/future.md)<br/>
