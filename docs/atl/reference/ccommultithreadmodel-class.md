---
title: Clase CComMultiThreadModel
ms.date: 11/04/2016
f1_keywords:
- CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModel::CriticalSection
- ATLBASE/ATL::CComMultiThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModel::Decrement
- ATLBASE/ATL::CComMultiThreadModel::Increment
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModel class
- threading [ATL]
ms.assetid: db8f1662-2f7a-44b3-b341-ffbfb6e422a3
ms.openlocfilehash: 7ef803439d2d683633e8f9c00810542dd787541e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327667"
---
# <a name="ccommultithreadmodel-class"></a>Clase CComMultiThreadModel

`CComMultiThreadModel`proporciona métodos seguros para subprocesos para incrementar y disminuir el valor de una variable.

## <a name="syntax"></a>Sintaxis

```
class CComMultiThreadModel
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|Referencias clase [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md).|
|[CComMultiThreadModel::CriticalSection](#criticalsection)|Referencias clase [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).|
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|Referencias clase [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComMultiThreadModel::Decrement](#decrement)|(Estático) Disminuye el valor de la variable especificada de una manera segura para subprocesos.|
|[CComMultiThreadModel::Increment](#increment)|(Estático) Incrementa el valor de la variable especificada de una manera segura para subprocesos.|

## <a name="remarks"></a>Observaciones

Normalmente, se `CComMultiThreadModel` usa a través de uno de los dos nombres **typedef,** ya sea [CComObjectThreadModel](atl-typedefs.md-ccomobjectthreadmodel o [CComGlobalsThreadModel](atl-typedefs.md-ccomglobalsthreadmodel. La clase a la que hace referencia cada **typedef** depende del modelo de subprocesos utilizado, como se muestra en la tabla siguiente:

|typedef|Roscado único|Roscado de apartamentos|Roscado libre|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S `CComSingleThreadModel`- ; M-`CComMultiThreadModel`

`CComMultiThreadModel`sí mismo define tres nombres **typedef.** `AutoCriticalSection`y `CriticalSection` clases de referencia que proporcionan métodos para obtener y liberar la propiedad de una sección crítica. `ThreadModelNoCS`referencia a la clase [CComMultiThreadModelNoCS(ccommultithreadmodelnocs-class.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="ccommultithreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CComMultiThreadModel::AutoCriticalSection

Cuando `CComMultiThreadModel`se usa , `AutoCriticalSection` el nombre **typedef** hace referencia a la clase [CComAutoCriticalSection](ccomautocriticalsection-class.md), que proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.

```
typedef CComAutoCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Observaciones

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) y [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) también `AutoCriticalSection`contienen definiciones para . En la tabla siguiente se muestra la relación entre la `AutoCriticalSection`clase de modelo de subprocesos y la clase de sección crítica a la que hace referencia:

|Clase definida en|Clase a la que se hace referencia|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Además `AutoCriticalSection`de , puede utilizar el nombre **typedef** [CriticalSection](#criticalsection). No debe `AutoCriticalSection` especificar en objetos globales o miembros de clase estática si desea eliminar el código de inicio de CRT.

### <a name="example"></a>Ejemplo

El código siguiente se modela después de `AutoCriticalSection` [CComObjectRootEx](ccomobjectrootex-class.md)y se muestra que se usa en un entorno de subprocesos.

```cpp
template<class ThreadModel>
class CMyAutoCritClass
{
public:
   typedef ThreadModel _ThreadModel;
   typedef typename _ThreadModel::AutoCriticalSection _CritSec;

   CMyAutoCritClass() : m_dwRef(0) {}

   ULONG InternalAddRef()
   {
      return _ThreadModel::Increment(&m_dwRef);
   }
   ULONG InternalRelease()
   {
      return _ThreadModel::Decrement(&m_dwRef);
   }
   void Lock() { m_critsec.Lock( ); }
   void Unlock() { m_critsec.Unlock(); }

private:
   _CritSec m_critsec;
   LONG m_dwRef;
```

En las tablas siguientes `InternalAddRef` `Lock` se muestran los `ThreadModel` resultados de los métodos y, según el parámetro de plantilla y el modelo de subprocesamiento utilizado por la aplicación:

### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel - CComObjectThreadModel

|Método|Rosca de uno o de apartamento|Rosca libre|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|El incremento no es seguro para subprocesos.|El incremento es seguro para subprocesos.|
|`Lock`|No hace nada; no hay ninguna sección crítica para bloquear.|La sección crítica está bloqueada.|

### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel á CComObjectThreadModel::ThreadModelNoCS

|Método|Rosca de uno o de apartamento|Rosca libre|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|El incremento no es seguro para subprocesos.|El incremento es seguro para subprocesos.|
|`Lock`|No hace nada; no hay ninguna sección crítica para bloquear.|No hace nada; no hay ninguna sección crítica para bloquear.|

## <a name="ccommultithreadmodelcriticalsection"></a><a name="criticalsection"></a>CComMultiThreadModel::CriticalSection

Cuando `CComMultiThreadModel`se usa , `CriticalSection` el nombre **typedef** hace referencia a la clase [CComCriticalSection](ccomcriticalsection-class.md), que proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.

```
typedef CComCriticalSection CriticalSection;
```

### <a name="remarks"></a>Observaciones

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) y [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) también `CriticalSection`contienen definiciones para . En la tabla siguiente se muestra la relación entre la `CriticalSection`clase de modelo de subprocesos y la clase de sección crítica a la que hace referencia:

|Clase definida en|Clase a la que se hace referencia|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Además `CriticalSection`de , puede utilizar el nombre **typedef** [AutoCriticalSection](#autocriticalsection). No debe `AutoCriticalSection` especificar en objetos globales o miembros de clase estática si desea eliminar el código de inicio de CRT.

### <a name="example"></a>Ejemplo

Vea [CComMultiThreadModel::AutoCriticalSection](#autocriticalsection).

## <a name="ccommultithreadmodeldecrement"></a><a name="decrement"></a>CComMultiThreadModel::Decrement

Esta función estática llama a la función Win32 [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement), que disminuye el valor de la variable señalada por *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
[en] Puntero a la variable que se va a disminuir.

### <a name="return-value"></a>Valor devuelto

Si el resultado del decremento `Decrement` es 0, devuelve 0. Si el resultado de la disminución es distinto de cero, el valor devuelto también es distinto de cero, pero puede no ser igual al resultado del decremento.

### <a name="remarks"></a>Observaciones

`InterlockedDecrement`impide que más de un subproceso utilice simultáneamente esta variable.

## <a name="ccommultithreadmodelincrement"></a><a name="increment"></a>CComMultiThreadModel::Increment

Esta función estática llama a la función Win32 [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement), que incrementa el valor de la variable señalada por *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw ();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
[en] Puntero a la variable que se va a incrementar.

### <a name="return-value"></a>Valor devuelto

Si el resultado del incremento `Increment` es 0, devuelve 0. Si el resultado del incremento es distinto de cero, el valor devuelto también es distinto de cero, pero puede no ser igual al resultado del incremento.

### <a name="remarks"></a>Observaciones

`InterlockedIncrement`impide que más de un subproceso utilice simultáneamente esta variable.

## <a name="ccommultithreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComMultiThreadModel::ThreadModelNoCS

Cuando `CComMultiThreadModel`se utiliza , `ThreadModelNoCS` el nombre **typedef** hace referencia a la clase [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md).

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Observaciones

`CComMultiThreadModelNoCS`proporciona métodos seguros para subprocesos para incrementar y disminuir una variable; sin embargo, no proporciona una sección crítica.

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) `CComMultiThreadModelNoCS` y también contienen definiciones para `ThreadModelNoCS`. En la tabla siguiente se muestra la relación entre `ThreadModelNoCS`la clase de modelo de subprocesamiento y la clase a la que hace referencia:

|Clase definida en|Clase a la que se hace referencia|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Ejemplo

Vea [CComMultiThreadModel::AutoCriticalSection](#autocriticalsection).

## <a name="see-also"></a>Consulte también

[Clase CComSingleThreadModel](ccomsinglethreadmodel-class.md)<br/>
[Clase CComAutoCriticalSection](ccomautocriticalsection-class.md)<br/>
[Clase CComCriticalSection](ccomcriticalsection-class.md)<br/>
[Información general de clases](../atl-class-overview.md)
