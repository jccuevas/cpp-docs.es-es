---
title: Clase CComSingleThreadModel
ms.date: 2/29/2020
f1_keywords:
- CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComSingleThreadModel::CriticalSection
- ATLBASE/ATL::CComSingleThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComSingleThreadModel::Decrement
- ATLBASE/ATL::CComSingleThreadModel::Increment
helpviewer_keywords:
- single-threaded applications
- CComSingleThreadModel class
- single-threaded applications, ATL
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
ms.openlocfilehash: 3d8169c999ba96049bc711033f7ba2ef53989663
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327326"
---
# <a name="ccomsinglethreadmodel-class"></a>Clase CComSingleThreadModel

Esta clase proporciona métodos para incrementar y disminuir el valor de una variable.

## <a name="syntax"></a>Sintaxis

```
class CComSingleThreadModel
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|Referencias clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComSingleThreadModel::CriticalSection](#criticalsection)|Referencias `CComFakeCriticalSection`clase .|
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|Referencias `CComSingleThreadModel`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComSingleThreadModel::Decrement](#decrement)|Disminuye el valor de la variable especificada. Esta implementación no es segura para subprocesos.|
|[CComSingleThreadModel::Increment](#increment)|Incrementa el valor de la variable especificada. Esta implementación no es segura para subprocesos.|

## <a name="remarks"></a>Observaciones

`CComSingleThreadModel`proporciona métodos para incrementar y disminuir el valor de una variable. A diferencia de [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), estos métodos no son seguros para subprocesos.

Normalmente, se `CComSingleThreadModel` usa a través de uno de los dos nombres **typedef,** [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) o [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel). La clase a la que hace referencia cada **typedef** depende del modelo de subprocesos utilizado, como se muestra en la tabla siguiente:

|typedef|Modelo de roscado único|Modelo de roscado de apartamentos|Modelo de roscado libre|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S `CComSingleThreadModel`- ; M-`CComMultiThreadModel`

`CComSingleThreadModel`sí mismo define tres nombres **typedef.** `ThreadModelNoCS`referencias `CComSingleThreadModel`. `AutoCriticalSection`y `CriticalSection` la clase de referencia [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), que proporciona métodos vacíos asociados con la obtención y liberación de la propiedad de una sección crítica.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="ccomsinglethreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CComSingleThreadModel::AutoCriticalSection

Cuando `CComSingleThreadModel`se utiliza , `AutoCriticalSection` el nombre **typedef** hace referencia a la clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Observaciones

Dado `CComFakeCriticalSection` que no proporciona una sección crítica, sus métodos no hacen nada.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) contienen definiciones para `AutoCriticalSection`. En la tabla siguiente se muestra la relación entre la `AutoCriticalSection`clase de modelo de subprocesos y la clase de sección crítica a la que hace referencia:

|Clase definida en|Clase a la que se hace referencia|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Además `AutoCriticalSection`de , puede utilizar el nombre **typedef** [CriticalSection](#criticalsection). No debe `AutoCriticalSection` especificar en objetos globales o miembros de clase estática si desea eliminar el código de inicio de CRT.

### <a name="example"></a>Ejemplo

Vea [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccomsinglethreadmodelcriticalsection"></a><a name="criticalsection"></a>CComSingleThreadModel::CriticalSection

Cuando `CComSingleThreadModel`se utiliza , `CriticalSection` el nombre **typedef** hace referencia a la clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Observaciones

Dado `CComFakeCriticalSection` que no proporciona una sección crítica, sus métodos no hacen nada.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) contienen definiciones para `CriticalSection`. En la tabla siguiente se muestra la relación entre la `CriticalSection`clase de modelo de subprocesos y la clase de sección crítica a la que hace referencia:

|Clase definida en|Clase a la que se hace referencia|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Además `CriticalSection`de , puede utilizar el nombre **typedef** [AutoCriticalSection](#autocriticalsection). No debe `AutoCriticalSection` especificar en objetos globales o miembros de clase estática si desea eliminar el código de inicio de CRT.

### <a name="example"></a>Ejemplo

Vea [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccomsinglethreadmodeldecrement"></a><a name="decrement"></a>CComSingleThreadModel::Decrement

Esta función estática disminuye el valor de la variable señalada por *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
[en] Puntero a la variable que se va a disminuir.

### <a name="return-value"></a>Valor devuelto

El resultado de la disminución.

## <a name="ccomsinglethreadmodelincrement"></a><a name="increment"></a>CComSingleThreadModel::Increment

Esta función estática incrementa el valor de la variable a la que apunta *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
[en] Puntero a la variable que se va a incrementar.

### <a name="return-value"></a>Valor devuelto

El resultado del incremento.

## <a name="ccomsinglethreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComSingleThreadModel::ThreadModelNoCS

Cuando `CComSingleThreadModel`se utiliza , `ThreadModelNoCS` el `CComSingleThreadModel`nombre **typedef** simplemente hace referencia a .

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>Observaciones

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) contienen definiciones para `ThreadModelNoCS`. En la tabla siguiente se muestra la relación entre `ThreadModelNoCS`la clase de modelo de subprocesamiento y la clase a la que hace referencia:

|Clase definida en|Clase a la que se hace referencia|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Ejemplo

Vea [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
