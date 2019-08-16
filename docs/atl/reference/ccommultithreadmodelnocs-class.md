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
ms.openlocfilehash: 01c7f953b6b8916394ee4c2b5b27cf84af52b920
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497080"
---
# <a name="ccommultithreadmodelnocs-class"></a>Clase CComMultiThreadModelNoCS

`CComMultiThreadModelNoCS`proporciona métodos seguros para subprocesos para aumentar y disminuir el valor de una variable, sin la funcionalidad crítica de bloqueo o desbloqueo de la sección.

## <a name="syntax"></a>Sintaxis

```
class CComMultiThreadModelNoCS
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|Clase de referencias [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComMultiThreadModelNoCS::CriticalSection](#criticalsection)|Clase `CComFakeCriticalSection`References.|
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|Clase `CComMultiThreadModelNoCS`References.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComMultiThreadModelNoCS::Decrement](#decrement)|Estático Disminuye el valor de la variable especificada de una manera segura para subprocesos.|
|[CComMultiThreadModelNoCS::Increment](#increment)|Estático Incrementa el valor de la variable especificada de una manera segura para subprocesos.|

## <a name="remarks"></a>Comentarios

`CComMultiThreadModelNoCS`es similar a [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) , ya que proporciona métodos seguros para subprocesos para aumentar y disminuir una variable. Sin embargo, cuando se hace referencia a una clase `CComMultiThreadModelNoCS`de sección crítica a `Lock` través `Unlock` de, los métodos como y no hacen nada.

Normalmente, se usa `CComMultiThreadModelNoCS` mediante el `ThreadModelNoCS` nombre **typedef** . Esta **definición** de tipo se `CComMultiThreadModelNoCS`define `CComMultiThreadModel`en, y [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md).

> [!NOTE]
>  Los nombres de **typedef** globales [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) y [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel) no hacen `CComMultiThreadModelNoCS`referencia a.

Además `ThreadModelNoCS`de, `CComMultiThreadModelNoCS` define `AutoCriticalSection` y. `CriticalSection` Estos dos últimos nombres **typedef** hacen referencia a [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), que proporciona métodos vacíos asociados a la obtención y liberación de una sección crítica.

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

##  <a name="autocriticalsection"></a>  CComMultiThreadModelNoCS::AutoCriticalSection

Al usar `CComMultiThreadModelNoCS`, el nombre `AutoCriticalSection` typedef hace referencia a la clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Comentarios

Dado `CComFakeCriticalSection` que no proporciona una sección crítica, sus métodos no hacen nada.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) también contienen definiciones para `AutoCriticalSection`. En la tabla siguiente se muestra la relación entre la clase de modelo de subprocesos y la clase `AutoCriticalSection`de sección crítica a la que se hace referencia:

|Clase definida en|Clase a la que se hace referencia|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Además `AutoCriticalSection`de, puede usar el nombre **typedef** [CriticalSection](#criticalsection). No debe especificar `AutoCriticalSection` en objetos globales o miembros de clase estática Si desea eliminar el código de inicio de CRT.

### <a name="example"></a>Ejemplo

Vea [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="criticalsection"></a>  CComMultiThreadModelNoCS::CriticalSection

Al usar `CComMultiThreadModelNoCS`, el nombre `CriticalSection` typedef hace referencia a la clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Comentarios

Dado `CComFakeCriticalSection` que no proporciona una sección crítica, sus métodos no hacen nada.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) también contienen definiciones para `CriticalSection`. En la tabla siguiente se muestra la relación entre la clase de modelo de subprocesos y la clase `CriticalSection`de sección crítica a la que se hace referencia:

|Clase definida en|Clase a la que se hace referencia|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Además `CriticalSection`de, puede usar el nombre `AutoCriticalSection` **typedef** . No debe especificar `AutoCriticalSection` en objetos globales o miembros de clase estática Si desea eliminar el código de inicio de CRT.

### <a name="example"></a>Ejemplo

Vea [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="decrement"></a>  CComMultiThreadModelNoCS::Decrement

Esta función estática llama a la función [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement)de Win32, que disminuye el valor de la variable a la que apunta *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
de Puntero a la variable que se va a reducir.

### <a name="return-value"></a>Valor devuelto

Si el resultado del decremento es 0, `Decrement` devuelve 0. Si el resultado del decremento es distinto de cero, el valor devuelto también es distinto de cero, pero puede no ser igual que el resultado de la disminución.

### <a name="remarks"></a>Comentarios

**InterlockedDecrement** impide que más de un subproceso use esta variable simultáneamente.

##  <a name="increment"></a>  CComMultiThreadModelNoCS::Increment

Esta función estática llama a la función [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement)de Win32, que incrementa el valor de la variable a la que apunta *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
de Puntero a la variable que se va a incrementar.

### <a name="return-value"></a>Valor devuelto

Si el resultado del incremento es 0, **Increment** devuelve 0. Si el resultado del incremento es distinto de cero, el valor devuelto también es distinto de cero, pero puede no ser igual al resultado del incremento.

### <a name="remarks"></a>Comentarios

**InterlockedIncrement** impide que más de un subproceso use esta variable simultáneamente.

##  <a name="threadmodelnocs"></a>  CComMultiThreadModelNoCS::ThreadModelNoCS

Al usar `CComMultiThreadModelNoCS`, el nombre `ThreadModelNoCS` typedef simplemente hace `CComMultiThreadModelNoCS`referencia a.

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Comentarios

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) también contienen definiciones para `ThreadModelNoCS`. En la tabla siguiente se muestra la relación entre la clase de modelo de subprocesos y `ThreadModelNoCS`la clase a la que hace referencia:

|Clase definida en|Clase a la que se hace referencia|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

Tenga en cuenta que la `ThreadModelNoCS` definición `CComMultiThreadModelNoCS` de en proporciona `CComMultiThreadModel` simetría `CComSingleThreadModel`con y. Por ejemplo, supongamos que el `CComMultiThreadModel::AutoCriticalSection` código de ejemplo de declara el siguiente **typedef**:

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

Independientemente de la clase especificada para `ThreadModel` ( `CComMultiThreadModelNoCS`como), `_ThreadModel` se resuelve en consecuencia.

### <a name="example"></a>Ejemplo

Vea [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
