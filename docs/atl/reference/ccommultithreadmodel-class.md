---
title: CComMultiThreadModel (clase)
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
ms.openlocfilehash: 2ec83fc320d65f5f51c14f9523544972cd69c66c
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328693"
---
# <a name="ccommultithreadmodel-class"></a>CComMultiThreadModel (clase)

`CComMultiThreadModel` Proporciona métodos seguros para subprocesos para aumentar y disminuir el valor de una variable.

## <a name="syntax"></a>Sintaxis

```
class CComMultiThreadModel
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|nombre|Descripción|
|----------|-----------------|
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|Hace referencia a clase [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md).|
|[CComMultiThreadModel::CriticalSection](#criticalsection)|Hace referencia a clase [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).|
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|Hace referencia a clase [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).|

### <a name="public-methods"></a>Métodos públicos

|nombre|Descripción|
|----------|-----------------|
|[CComMultiThreadModel::Decrement](#decrement)|(Estático) Disminuye el valor de la variable especificada de una manera segura para subprocesos.|
|[CComMultiThreadModel::Increment](#increment)|(Estático) Incrementa el valor de la variable especificada de una manera segura para subprocesos.|

## <a name="remarks"></a>Comentarios

Normalmente, se utiliza `CComMultiThreadModel` a través de uno de los dos **typedef** nombres, ya sea [CComObjectThreadModel] (atl-typedefs.md #ccomobjectthreadmodel o [CComGlobalsThreadModel] (atl-typedefs.md #ccomglobalsthreadmodel. La clase que se hace referencia a cada uno de ellos **typedef** depende del modelo de subprocesos utilizado, tal como se muestra en la tabla siguiente:

|typedef|Subprocesamiento único|Apartamento de subproceso|Subprocesamiento libre|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S= `CComSingleThreadModel`; M= `CComMultiThreadModel`

`CComMultiThreadModel` Sí define tres **typedef** nombres. `AutoCriticalSection` y `CriticalSection` hacen referencia a las clases que proporcionan métodos para obtener y liberar la propiedad de una sección crítica. `ThreadModelNoCS` las referencias de clase [CComMultiThreadModelNoCS(ccommultithreadmodelnocs-class.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="autocriticalsection"></a>  CComMultiThreadModel::AutoCriticalSection

Cuando se usa `CComMultiThreadModel`, **typedef** nombre `AutoCriticalSection` hace referencia a clase [CComAutoCriticalSection](ccomautocriticalsection-class.md), que proporciona métodos para obtener y liberar la propiedad de una sección crítica objeto.

```
typedef CComAutoCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Comentarios

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) y [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) también contienen las definiciones para `AutoCriticalSection`. En la tabla siguiente se muestra la relación entre la clase del modelo de subprocesos y la clase de sección crítica al que hace referencia `AutoCriticalSection`:

|Clase definida en|Clase que se hace referenciada|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Además `AutoCriticalSection`, puede usar el **typedef** nombre [CriticalSection](#criticalsection). No se debe especificar `AutoCriticalSection` en objetos globales o miembros de clase estáticos si desea eliminar el código de inicio de CRT.

### <a name="example"></a>Ejemplo

El código siguiente se modela después [CComObjectRootEx](ccomobjectrootex-class.md)y muestra `AutoCriticalSection` que se va a usar en un entorno de subprocesamiento.

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

Las siguientes tablas muestran los resultados de la `InternalAddRef` y `Lock` métodos, según la `ThreadModel` parámetro de plantilla y el modelo de subprocesos utilizado por la aplicación:

### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel

|Método|Único o apartamento de subproceso|Subprocesamiento libre|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|El incremento no es segura para subprocesos.|El incremento es segura para subprocesos.|
|`Lock`|No hace nada; No hay ninguna sección crítica para bloquear.|La sección crítica está bloqueada.|

### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel::ThreadModelNoCS

|Método|Único o apartamento de subproceso|Subprocesamiento libre|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|El incremento no es segura para subprocesos.|El incremento es segura para subprocesos.|
|`Lock`|No hace nada; No hay ninguna sección crítica para bloquear.|No hace nada; No hay ninguna sección crítica para bloquear.|

##  <a name="criticalsection"></a>  CComMultiThreadModel::CriticalSection

Cuando se usa `CComMultiThreadModel`, **typedef** nombre `CriticalSection` hace referencia a clase [CComCriticalSection](ccomcriticalsection-class.md), que proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.

```
typedef CComCriticalSection CriticalSection;
```

### <a name="remarks"></a>Comentarios

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) y [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) también contienen las definiciones para `CriticalSection`. En la tabla siguiente se muestra la relación entre la clase del modelo de subprocesos y la clase de sección crítica al que hace referencia `CriticalSection`:

|Clase definida en|Clase que se hace referenciada|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Además `CriticalSection`, puede usar el **typedef** nombre [AutoCriticalSection](#autocriticalsection). No se debe especificar `AutoCriticalSection` en objetos globales o miembros de clase estáticos si desea eliminar el código de inicio de CRT.

### <a name="example"></a>Ejemplo

Consulte [CComMultiThreadModel::AutoCriticalSection](#autocriticalsection).

##  <a name="decrement"></a>  CComMultiThreadModel::Decrement

Esta función estática llama a la función de Win32 [InterlockedDecrement](/windows/desktop/api/winnt/nf-winnt-interlockeddecrement), que disminuye el valor de la variable apunta a *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
[in] Puntero a la variable que se va a reducir.

### <a name="return-value"></a>Valor devuelto

Si el resultado de la reducción es 0, a continuación, `Decrement` devuelve 0. Si el resultado de la reducción es distinto de cero, el valor devuelto también es distinto de cero, pero no puede ser igual al resultado de la reducción.

### <a name="remarks"></a>Comentarios

`InterlockedDecrement` impide que varios subprocesos simultáneamente mediante esta variable.

##  <a name="increment"></a>  CComMultiThreadModel::Increment

Esta función estática llama a la función de Win32 [InterlockedIncrement](/windows/desktop/api/winnt/nf-winnt-interlockedincrement), lo que incrementa el valor de la variable apuntado *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw ();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
[in] Puntero a la variable que se va a incrementar.

### <a name="return-value"></a>Valor devuelto

Si el resultado del incremento es 0, a continuación, `Increment` devuelve 0. Si el resultado del incremento es distinto de cero, el valor devuelto también es distinto de cero, pero no puede ser igual al resultado del incremento.

### <a name="remarks"></a>Comentarios

`InterlockedIncrement` impide que varios subprocesos simultáneamente mediante esta variable.

##  <a name="threadmodelnocs"></a>  CComMultiThreadModel::ThreadModelNoCS

Cuando se usa `CComMultiThreadModel`, **typedef** nombre `ThreadModelNoCS` hace referencia a clase [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md).

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Comentarios

`CComMultiThreadModelNoCS` Proporciona métodos de subprocesos para aumentar y disminuir una variable; Sin embargo, no proporciona una sección crítica.

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) y `CComMultiThreadModelNoCS` también contienen las definiciones para `ThreadModelNoCS`. En la tabla siguiente se muestra la relación entre la clase del modelo de subprocesos y la clase al que hace referencia `ThreadModelNoCS`:

|Clase definida en|Clase que se hace referenciada|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Ejemplo

Consulte [CComMultiThreadModel::AutoCriticalSection](#autocriticalsection).

## <a name="see-also"></a>Vea también

[CComSingleThreadModel (clase)](ccomsinglethreadmodel-class.md)<br/>
[CComAutoCriticalSection (clase)](ccomautocriticalsection-class.md)<br/>
[CComCriticalSection (clase)](ccomcriticalsection-class.md)<br/>
[Información general de clases](../atl-class-overview.md)
