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
ms.openlocfilehash: 74fb68eead498685ef252968124368863e27be75
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497101"
---
# <a name="ccommultithreadmodel-class"></a>Clase CComMultiThreadModel

`CComMultiThreadModel`proporciona métodos seguros para subprocesos para aumentar y disminuir el valor de una variable.

## <a name="syntax"></a>Sintaxis

```
class CComMultiThreadModel
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|Clase de referencias [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md).|
|[CComMultiThreadModel::CriticalSection](#criticalsection)|Clase de referencias [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).|
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|Clase de referencias [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComMultiThreadModel::Decrement](#decrement)|Estático Disminuye el valor de la variable especificada de una manera segura para subprocesos.|
|[CComMultiThreadModel::Increment](#increment)|Estático Incrementa el valor de la variable especificada de una manera segura para subprocesos.|

## <a name="remarks"></a>Comentarios

Normalmente, se usa `CComMultiThreadModel` a través de uno de los dos nombres **typedef** , ya sea [CComObjectThreadModel] (ATL-typedefs. MD # CComObjectThreadModel o [CComGlobalsThreadModel] (ATL-typedefs. MD # CComGlobalsThreadModel. La clase a la que hace referencia cada **typedef** depende del modelo de subprocesos utilizado, tal como se muestra en la tabla siguiente:

|typedef|Subprocesamiento único|Subprocesamiento de apartamento|Subprocesamiento libre|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M =`CComMultiThreadModel`

`CComMultiThreadModel`define tres nombres de **typedef** . `AutoCriticalSection`y `CriticalSection` las clases de referencia que proporcionan métodos para obtener y liberar la propiedad de una sección crítica. `ThreadModelNoCS`clase References [CComMultiThreadModelNoCS (CComMultiThreadModelNoCS-class.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

##  <a name="autocriticalsection"></a>  CComMultiThreadModel::AutoCriticalSection

Al usar `CComMultiThreadModel`, el nombre `AutoCriticalSection` typedef hace referencia a la clase [CComAutoCriticalSection](ccomautocriticalsection-class.md), que proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.

```
typedef CComAutoCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Comentarios

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) y [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) también contienen definiciones para `AutoCriticalSection`. En la tabla siguiente se muestra la relación entre la clase de modelo de subprocesos y la clase `AutoCriticalSection`de sección crítica a la que se hace referencia:

|Clase definida en|Clase a la que se hace referencia|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Además `AutoCriticalSection`de, puede usar el nombre **typedef** [CriticalSection](#criticalsection). No debe especificar `AutoCriticalSection` en objetos globales o miembros de clase estática Si desea eliminar el código de inicio de CRT.

### <a name="example"></a>Ejemplo

El siguiente código se modela después de [CComObjectRootEx](ccomobjectrootex-class.md)y demuestra `AutoCriticalSection` su uso en un entorno de subprocesos.

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

En las tablas siguientes se muestran los resultados `InternalAddRef` de `Lock` los métodos y, dependiendo del `ThreadModel` parámetro de plantilla y del modelo de subprocesos que usa la aplicación:

### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel

|Método|Subprocesamiento de un solo apartamento|Subprocesamiento libre|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|El incremento no es seguro para subprocesos.|El incremento es seguro para subprocesos.|
|`Lock`|No hace nada; no hay ninguna sección crítica para bloquear.|La sección crítica está bloqueada.|

### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel::ThreadModelNoCS

|Método|Subprocesamiento de un solo apartamento|Subprocesamiento libre|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|El incremento no es seguro para subprocesos.|El incremento es seguro para subprocesos.|
|`Lock`|No hace nada; no hay ninguna sección crítica para bloquear.|No hace nada; no hay ninguna sección crítica para bloquear.|

##  <a name="criticalsection"></a>  CComMultiThreadModel::CriticalSection

Al usar `CComMultiThreadModel`, el nombre `CriticalSection` typedef hace referencia a la clase [CComCriticalSection](ccomcriticalsection-class.md), que proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.

```
typedef CComCriticalSection CriticalSection;
```

### <a name="remarks"></a>Comentarios

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) y [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) también contienen definiciones para `CriticalSection`. En la tabla siguiente se muestra la relación entre la clase de modelo de subprocesos y la clase `CriticalSection`de sección crítica a la que se hace referencia:

|Clase definida en|Clase a la que se hace referencia|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Además `CriticalSection`de, puede usar el nombre **typedef** [AutoCriticalSection](#autocriticalsection). No debe especificar `AutoCriticalSection` en objetos globales o miembros de clase estática Si desea eliminar el código de inicio de CRT.

### <a name="example"></a>Ejemplo

Vea [CComMultiThreadModel:: AutoCriticalSection](#autocriticalsection).

##  <a name="decrement"></a>  CComMultiThreadModel::Decrement

Esta función estática llama a la función [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement)de Win32, que disminuye el valor de la variable a la que apunta *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
de Puntero a la variable que se va a reducir.

### <a name="return-value"></a>Valor devuelto

Si el resultado del decremento es 0, `Decrement` devuelve 0. Si el resultado del decremento es distinto de cero, el valor devuelto también es distinto de cero, pero puede no ser igual que el resultado de la disminución.

### <a name="remarks"></a>Comentarios

`InterlockedDecrement`impide que más de un subproceso utilice esta variable simultáneamente.

##  <a name="increment"></a>  CComMultiThreadModel::Increment

Esta función estática llama a la función [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement)de Win32, que incrementa el valor de la variable a la que apunta *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw ();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
de Puntero a la variable que se va a incrementar.

### <a name="return-value"></a>Valor devuelto

Si el resultado del incremento es 0, `Increment` devuelve 0. Si el resultado del incremento es distinto de cero, el valor devuelto también es distinto de cero, pero puede no ser igual al resultado del incremento.

### <a name="remarks"></a>Comentarios

`InterlockedIncrement`impide que más de un subproceso utilice esta variable simultáneamente.

##  <a name="threadmodelnocs"></a>  CComMultiThreadModel::ThreadModelNoCS

Al usar `CComMultiThreadModel`, el nombre `ThreadModelNoCS` typedef hace referencia a la clase [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md).

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Comentarios

`CComMultiThreadModelNoCS`proporciona métodos seguros para subprocesos para aumentar y disminuir una variable; sin embargo, no proporciona una sección crítica.

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) y `CComMultiThreadModelNoCS` también contienen definiciones para `ThreadModelNoCS`. En la tabla siguiente se muestra la relación entre la clase de modelo de subprocesos y `ThreadModelNoCS`la clase a la que hace referencia:

|Clase definida en|Clase a la que se hace referencia|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Ejemplo

Vea [CComMultiThreadModel:: AutoCriticalSection](#autocriticalsection).

## <a name="see-also"></a>Vea también

[CComSingleThreadModel (clase)](ccomsinglethreadmodel-class.md)<br/>
[CComAutoCriticalSection (clase)](ccomautocriticalsection-class.md)<br/>
[CComCriticalSection (clase)](ccomcriticalsection-class.md)<br/>
[Información general sobre clases](../atl-class-overview.md)
