---
title: shared_future (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- future/std::shared_future
- future/std::shared_future::shared_future
- future/std::shared_future::get
- future/std::shared_future::valid
- future/std::shared_future::wait
- future/std::shared_future::wait_for
- future/std::shared_future::wait_until
dev_langs:
- C++
ms.assetid: 454ebedd-f42b-405f-99a5-a25cc9ad7c90
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::shared_future [C++]
- std::shared_future [C++], shared_future
- std::shared_future [C++], get
- std::shared_future [C++], valid
- std::shared_future [C++], wait
- std::shared_future [C++], wait_for
- std::shared_future [C++], wait_until
ms.workload:
- cplusplus
ms.openlocfilehash: 7f022d48dcd5cbc8afa1b9d3100cd27c2ad12175
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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
|[espera](#wait)|Bloquea el subproceso actual hasta que el estado asincrónico asociado esté listo.|
|[wait_for](#wait_for)|Se bloquea hasta que el estado asincrónico asociado está listo, o bien hasta que el tiempo especificado haya transcurrido.|
|[wait_until](#wait_until)|Se bloquea hasta que el estado asincrónico asociado está listo o hasta un punto determinado en el tiempo.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[shared_future::operator=](#op_eq)|Asigna un nuevo estado asincrónico asociado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<futura >

**Espacio de nombres:** std

## <a name="get"></a>  shared_future:: Get

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

Dado que no existe ningún valor almacenado para la especialización `shared_future<void>`, el método devuelve `void`.

## <a name="op_eq"></a>  shared_future::operator=

Transfiere un *estado asincrónico asociado* de un objeto especificado.

```cpp
shared_future& operator=(shared_future&& Right) noexcept;
shared_future& operator=(const shared_future& Right);
```

### <a name="parameters"></a>Parámetros

`Right` Un `shared_future` objeto.

### <a name="return-value"></a>Valor devuelto

`*this`

### <a name="remarks"></a>Comentarios

Para el primer operador, después de la operación, `Right` ya no tiene un estado asincrónico asociado.

Para el segundo método, `Right` mantiene su estado asincrónico asociado.

## <a name="shared_future"></a>  shared_future::shared_future (Constructor)

Construye un objeto `shared_future`.

```cpp
shared_future() noexcept;
shared_future(future<Ty>&& Right) noexcept;
shared_future(shared_future&& Right) noexcept;
shared_future(const shared_future& Right);
```

### <a name="parameters"></a>Parámetros

`Right` A [futuras](../standard-library/future-class.md) o `shared_future` objeto.

### <a name="remarks"></a>Comentarios

El primer constructor crea un objeto `shared_future` que no tiene ningún *estado asincrónico asociado*.

El segundo y el tercer constructor crean un objeto `shared_future` y transfieren el estado asincrónico asociado de `Right`. `Right` ya no tiene un estado asincrónico asociado.

El cuarto constructor crea un objeto `shared_future` que tiene el mismo estado asincrónico asociado que `Right`.

## <a name="valid"></a>  shared_future:: Valid

Especifica si el objeto tiene un *estado asincrónico asociado*.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Valor devuelto

Es `true` si el objeto tiene un estado asincrónico asociado; de lo contrario, es `false`.

## <a name="wait"></a>  shared_future:: wait

Bloquea el subproceso actual hasta que el *estado asincrónico asociado* esté *listo*.

```cpp
void wait() const;
```

### <a name="remarks"></a>Comentarios

Un estado asincrónico asociado está listo solo si su proveedor asincrónico ha almacenado un valor devuelto o ha almacenado una excepción.

## <a name="wait_for"></a>  shared_future:: wait_for

Bloquea el subproceso actual hasta que el estado asincrónico asociado esté *listo* o hasta que haya transcurrido un tiempo especificado.

```cpp
template <class Rep, class Period>
future_status wait_for(
    const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parámetros

`Rel_time` A [chrono:: Duration](../standard-library/duration-class.md) objeto que especifica un intervalo de tiempo máximo que el subproceso se bloquea.

### <a name="return-value"></a>Valor devuelto

Un [future_status](../standard-library/future-enums.md#future_status) que indica el motivo que se va a devolver.

### <a name="remarks"></a>Comentarios

Un estado asincrónico asociado está *listo* únicamente si su proveedor asincrónico ha almacenado un valor devuelto o una excepción.

## <a name="wait_until"></a>  shared_future:: wait_until

Bloquea el subproceso actual hasta que el estado asincrónico asociado esté *listo* o hasta después de un punto de tiempo especificado.

```cpp
template <class Clock, class Duration>
future_status wait_until(
    const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parámetros

`Abs_time` A [chrono:: time_point](../standard-library/time-point-class.md) objeto que especifica un tiempo después del cual se puede desbloquear el subproceso.

### <a name="return-value"></a>Valor devuelto

Un [future_status](../standard-library/future-enums.md#future_status) que indica el motivo que se va a devolver.

### <a name="remarks"></a>Comentarios

Un estado asincrónico asociado está listo solo si su proveedor asincrónico ha almacenado un valor devuelto o ha almacenado una excepción.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<future>](../standard-library/future.md)<br/>
