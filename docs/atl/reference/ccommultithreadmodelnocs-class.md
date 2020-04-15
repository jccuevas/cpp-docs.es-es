---
title: Clase CComMultiThreadModelNoCS
ms.date: 11/04/2016
f1_keywords:
- CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::CriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::Decrement
- ATLBASE/ATL::CComMultiThreadModelNoCS::Increment
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModelNoCS class
- threading [ATL]
ms.assetid: 2b3f7a45-fd72-452c-aaf3-ccdaa621c821
ms.openlocfilehash: 4d41ffcfccbd7ef65ed86df79bffec1209a88cd3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327651"
---
# <a name="ccommultithreadmodelnocs-class"></a>Clase CComMultiThreadModelNoCS

`CComMultiThreadModelNoCS`proporciona métodos seguros para subprocesos para incrementar y disminuir el valor de una variable, sin bloqueo de sección crítica ni funcionalidad de desbloqueo.

## <a name="syntax"></a>Sintaxis

```
class CComMultiThreadModelNoCS
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|Referencias clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComMultiThreadModelNoCS::CriticalSection](#criticalsection)|Referencias `CComFakeCriticalSection`clase .|
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|Referencias `CComMultiThreadModelNoCS`clase .|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComMultiThreadModelNoCS::Decrement](#decrement)|(Estático) Disminuye el valor de la variable especificada de una manera segura para subprocesos.|
|[CComMultiThreadModelNoCS::Increment](#increment)|(Estático) Incrementa el valor de la variable especificada de una manera segura para subprocesos.|

## <a name="remarks"></a>Observaciones

`CComMultiThreadModelNoCS`es similar a [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) en que proporciona métodos seguros para subprocesos para incrementar y disminuir una variable. Sin embargo, cuando se `CComMultiThreadModelNoCS`hace referencia `Lock` a `Unlock` una clase de sección crítica a través de , métodos como y no hará nada.

Normalmente, se `CComMultiThreadModelNoCS` usa `ThreadModelNoCS` a través del nombre **typedef.** Esta **definición de** `CComMultiThreadModelNoCS`tipo `CComMultiThreadModel`se define en , , y [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md).

> [!NOTE]
> Los nombres **de tipo de tipo** global [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) y `CComMultiThreadModelNoCS` [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel) no hacen referencia a .

Además `ThreadModelNoCS` `CComMultiThreadModelNoCS` de `AutoCriticalSection` `CriticalSection`, define y . Estos dos últimos nombres **typedef** hacen referencia a [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), que proporciona métodos vacíos asociados con la obtención y liberación de una sección crítica.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="ccommultithreadmodelnocsautocriticalsection"></a><a name="autocriticalsection"></a>CComMultiThreadModelNoCS::AutoCriticalSection

Cuando `CComMultiThreadModelNoCS`se utiliza , `AutoCriticalSection` el nombre **typedef** hace referencia a la clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Observaciones

Dado `CComFakeCriticalSection` que no proporciona una sección crítica, sus métodos no hacen nada.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) también `AutoCriticalSection`contienen definiciones para . En la tabla siguiente se muestra la relación entre la `AutoCriticalSection`clase de modelo de subprocesos y la clase de sección crítica a la que hace referencia:

|Clase definida en|Clase a la que se hace referencia|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Además `AutoCriticalSection`de , puede utilizar el nombre **typedef** [CriticalSection](#criticalsection). No debe `AutoCriticalSection` especificar en objetos globales o miembros de clase estática si desea eliminar el código de inicio de CRT.

### <a name="example"></a>Ejemplo

Vea [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccommultithreadmodelnocscriticalsection"></a><a name="criticalsection"></a>CComMultiThreadModelNoCS::CriticalSection

Cuando `CComMultiThreadModelNoCS`se utiliza , `CriticalSection` el nombre **typedef** hace referencia a la clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Observaciones

Dado `CComFakeCriticalSection` que no proporciona una sección crítica, sus métodos no hacen nada.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) también `CriticalSection`contienen definiciones para . En la tabla siguiente se muestra la relación entre la `CriticalSection`clase de modelo de subprocesos y la clase de sección crítica a la que hace referencia:

|Clase definida en|Clase a la que se hace referencia|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Además `CriticalSection`de , puede utilizar `AutoCriticalSection`el nombre **typedef** . No debe `AutoCriticalSection` especificar en objetos globales o miembros de clase estática si desea eliminar el código de inicio de CRT.

### <a name="example"></a>Ejemplo

Vea [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccommultithreadmodelnocsdecrement"></a><a name="decrement"></a>CComMultiThreadModelNoCS::Decrement

Esta función estática llama a la función Win32 [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement), que disminuye el valor de la variable señalada por *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
[en] Puntero a la variable que se va a disminuir.

### <a name="return-value"></a>Valor devuelto

Si el resultado del decremento `Decrement` es 0, devuelve 0. Si el resultado de la disminución es distinto de cero, el valor devuelto también es distinto de cero, pero puede no ser igual al resultado del decremento.

### <a name="remarks"></a>Observaciones

**InterlockedDecrement** impide que más de un subproceso utilice simultáneamente esta variable.

## <a name="ccommultithreadmodelnocsincrement"></a><a name="increment"></a>CComMultiThreadModelNoCS::Increment

Esta función estática llama a la función Win32 [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement), que incrementa el valor de la variable señalada por *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
[en] Puntero a la variable que se va a incrementar.

### <a name="return-value"></a>Valor devuelto

Si el resultado del incremento es 0, **Increment** devuelve 0. Si el resultado del incremento es distinto de cero, el valor devuelto también es distinto de cero, pero puede no ser igual al resultado del incremento.

### <a name="remarks"></a>Observaciones

**InterlockedIncrement** impide que más de un subproceso utilice simultáneamente esta variable.

## <a name="ccommultithreadmodelnocsthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComMultiThreadModelNoCS::ThreadModelNoCS

Cuando `CComMultiThreadModelNoCS`se utiliza , `ThreadModelNoCS` el `CComMultiThreadModelNoCS`nombre **typedef** simplemente hace referencia a .

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Observaciones

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) también `ThreadModelNoCS`contienen definiciones para . En la tabla siguiente se muestra la relación entre `ThreadModelNoCS`la clase de modelo de subprocesamiento y la clase a la que hace referencia:

|Clase definida en|Clase a la que se hace referencia|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

Tenga en cuenta `ThreadModelNoCS` `CComMultiThreadModelNoCS` que la `CComMultiThreadModel` definición de in proporciona simetría con y `CComSingleThreadModel`. Por ejemplo, supongamos `CComMultiThreadModel::AutoCriticalSection` que el código de ejemplo declarado en el siguiente **typedef:**

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

Independientemente de la clase `ThreadModel` especificada `CComMultiThreadModelNoCS`para `_ThreadModel` (por ejemplo, ), se resuelve en consecuencia.

### <a name="example"></a>Ejemplo

Vea [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
