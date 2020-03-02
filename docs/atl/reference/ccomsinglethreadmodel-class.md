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
ms.openlocfilehash: 9b111e06ba475a5077ba36b2235e8bd530302189
ms.sourcegitcommit: ab8d7b47b63b62892a1256a09b1324a9a136eccf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2020
ms.locfileid: "78215459"
---
# <a name="ccomsinglethreadmodel-class"></a>Clase CComSingleThreadModel

Esta clase proporciona métodos para aumentar y disminuir el valor de una variable.

## <a name="syntax"></a>Sintaxis

```
class CComSingleThreadModel
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Typedefs públicos

|Name|Descripción|
|----------|-----------------|
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|Clase de referencias [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComSingleThreadModel:: CriticalSection](#criticalsection)|`CComFakeCriticalSection`de la clase References.|
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|Hace referencia `CComSingleThreadModel`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComSingleThreadModel::D ecrement](#decrement)|Disminuye el valor de la variable especificada. Esta implementación no es segura para subprocesos.|
|[CComSingleThreadModel:: Increment](#increment)|Incrementa el valor de la variable especificada. Esta implementación no es segura para subprocesos.|

## <a name="remarks"></a>Comentarios

`CComSingleThreadModel` proporciona métodos para aumentar y disminuir el valor de una variable. A diferencia de [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), estos métodos no son seguros para subprocesos.

Normalmente, se usa `CComSingleThreadModel` a través de uno de los dos nombres de **typedef** , ya sea [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) o [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel). La clase a la que hace referencia cada **typedef** depende del modelo de subprocesos utilizado, tal como se muestra en la tabla siguiente:

|typedef|Modelo de subprocesos únicos|Modelo de subprocesos de apartamento|Modelo de subprocesamiento libre|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M = `CComMultiThreadModel`

`CComSingleThreadModel` define tres nombres de **typedef** . `ThreadModelNoCS` hace referencia a `CComSingleThreadModel`. `AutoCriticalSection` y `CriticalSection` clase de referencia [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), que proporciona métodos vacíos asociados a la obtención y liberación de la propiedad de una sección crítica.

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

##  <a name="autocriticalsection"></a>CComSingleThreadModel::AutoCriticalSection

Al utilizar `CComSingleThreadModel`, el nombre **typedef** `AutoCriticalSection` hace referencia a la clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Comentarios

Dado que `CComFakeCriticalSection` no proporciona una sección crítica, sus métodos no hacen nada.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) contienen definiciones para `AutoCriticalSection`. En la tabla siguiente se muestra la relación entre la clase de modelo de subprocesos y la clase de sección crítica a la que hace referencia `AutoCriticalSection`:

|Clase definida en|Clase a la que se hace referencia|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Además de `AutoCriticalSection`, puede usar el nombre **typedef** [CriticalSection](#criticalsection). No debe especificar `AutoCriticalSection` en objetos globales o miembros de clase estática Si desea eliminar el código de inicio de CRT.

### <a name="example"></a>Ejemplo

Vea [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="criticalsection"></a>CComSingleThreadModel:: CriticalSection

Al utilizar `CComSingleThreadModel`, el nombre **typedef** `CriticalSection` hace referencia a la clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Comentarios

Dado que `CComFakeCriticalSection` no proporciona una sección crítica, sus métodos no hacen nada.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) contienen definiciones para `CriticalSection`. En la tabla siguiente se muestra la relación entre la clase de modelo de subprocesos y la clase de sección crítica a la que hace referencia `CriticalSection`:

|Clase definida en|Clase a la que se hace referencia|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Además de `CriticalSection`, puede usar el nombre **typedef** [AutoCriticalSection](#autocriticalsection). No debe especificar `AutoCriticalSection` en objetos globales o miembros de clase estática Si desea eliminar el código de inicio de CRT.

### <a name="example"></a>Ejemplo

Vea [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="decrement"></a>CComSingleThreadModel::D ecrement

Esta función estática reduce el valor de la variable a la que apunta *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
de Puntero a la variable que se va a reducir.

### <a name="return-value"></a>Valor devuelto

Resultado de la reducción.

##  <a name="increment"></a>CComSingleThreadModel:: Increment

Esta función estática incrementa el valor de la variable a la que apunta *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
de Puntero a la variable que se va a incrementar.

### <a name="return-value"></a>Valor devuelto

Resultado del incremento.

##  <a name="threadmodelnocs"></a>CComSingleThreadModel::ThreadModelNoCS

Al utilizar `CComSingleThreadModel`, el nombre de **typedef** `ThreadModelNoCS` simplemente hace referencia a `CComSingleThreadModel`.

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>Comentarios

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) contienen definiciones para `ThreadModelNoCS`. En la tabla siguiente se muestra la relación entre la clase de modelo de subprocesos y la clase a la que hace referencia `ThreadModelNoCS`:

|Clase definida en|Clase a la que se hace referencia|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Ejemplo

Vea [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
