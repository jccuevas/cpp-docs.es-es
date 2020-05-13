---
title: Clase CComAutoThreadModule
ms.date: 11/04/2016
f1_keywords:
- CComAutoThreadModule
- ATLBASE/ATL::CComAutoThreadModule
- ATLBASE/ATL::CreateInstance
- ATLBASE/ATL::GetDefaultThreads
- ATLBASE/ATL::Init
- ATLBASE/ATL::Lock
- ATLBASE/ATL::Unlock
- ATLBASE/ATL::dwThreadID
- ATLBASE/ATL::m_Allocator
- ATLBASE/ATL::m_nThreads
- ATLBASE/ATL::m_pApartments
helpviewer_keywords:
- CComAutoThreadModule class
- apartment model modules
ms.assetid: 13063ea5-a57e-4aac-97d3-227137262811
ms.openlocfilehash: 391354c5672cf15c0286491619a13c6005493cfa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321065"
---
# <a name="ccomautothreadmodule-class"></a>Clase CComAutoThreadModule

A partir de ATL `CComAutoThreadModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class ThreadAllocator = CComSimpleThreadAllocator>
class CComAutoThreadModule : public CComModule
```

#### <a name="parameters"></a>Parámetros

*ThreadAllocator*<br/>
[en] La clase que administra la selección de subprocesos. El valor predeterminado es [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[CreateInstance](#createinstance)|Selecciona un subproceso y, a continuación, crea un objeto en el apartamento asociado.|
|[GetDefaultThreads](#getdefaultthreads)|(Estático) Calcula dinámicamente el número de subprocesos para el módulo en función del número de procesadores.|
|[Init](#init)|Crea los subprocesos del módulo.|
|[Bloquear](#lock)|Incrementa el recuento de bloqueos en el módulo y en el subproceso actual.|
|[Desbloquear](#unlock)|Disminuye el recuento de bloqueoen el módulo y en el subproceso actual.|

### <a name="data-members"></a>Miembros de datos

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[dwThreadID](#dwthreadid)|Contiene el identificador del subproceso actual.|
|[m_Allocator](#m_allocator)|Administra la selección de subprocesos.|
|[m_nThreads](#m_nthreads)|Contiene el número de subprocesos del módulo.|
|[m_pApartments](#m_papartments)|Gestiona los apartamentos del módulo.|

## <a name="remarks"></a>Observaciones

> [!NOTE]
> Esta clase está obsoleta, habiendo sido reemplazada por el [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) y [CAtlModule](../../atl/reference/catlmodule-class.md) clases derivadas. La información siguiente es para su uso con versiones anteriores de ATL.

`CComAutoThreadModule`deriva de [CComModule](../../atl/reference/ccommodule-class.md) para implementar un servidor COM de modelo de apartamento con grupo de subprocesos para EXEs y servicios de Windows. `CComAutoThreadModule`utiliza [CComApartment](../../atl/reference/ccomapartment-class.md) para administrar un apartamento para cada subproceso en el módulo.

Derive el `CComAutoThreadModule` módulo de cuando desee crear objetos en varios apartamentos. También debe incluir la [macro DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) en la definición de clase del objeto para especificar [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) como generador de clases.

De forma predeterminada, el AppWizard COM de ATL (el Asistente para `CComModule`proyectos ATL en Visual Studio .NET) derivará el módulo de . Para `CComAutoThreadModule`utilizar , modifique la definición de clase. Por ejemplo:

[!code-cpp[NVC_ATL_AxHost#2](../../atl/codesnippet/cpp/ccomautothreadmodule-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`IAtlAutoThreadModule`

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

[CComModule](../../atl/reference/ccommodule-class.md)

`CComAutoThreadModule`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="ccomautothreadmodulecreateinstance"></a><a name="createinstance"></a>CComAutoThreadModule::CreateInstance

A partir de ATL `CComAutoThreadModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>Parámetros

*pfnCreateInstance*<br/>
[en] Un puntero a una función de creador.

*riid*<br/>
[en] El IID de la interfaz solicitada.

*ppvObj*<br/>
[fuera] Un puntero al puntero de interfaz identificado por *riid*. Si el objeto no admite esta interfaz, *ppvObj* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Selecciona un subproceso y, a continuación, crea un objeto en el apartamento asociado.

## <a name="ccomautothreadmoduledwthreadid"></a><a name="dwthreadid"></a>CComAutoThreadModule::dwThreadID

A partir de ATL `CComAutoThreadModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
DWORD dwThreadID;
```

### <a name="remarks"></a>Observaciones

Contiene el identificador del subproceso actual.

## <a name="ccomautothreadmodulegetdefaultthreads"></a><a name="getdefaultthreads"></a>CComAutoThreadModule::GetDefaultThreads

A partir de ATL `CComAutoThreadModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Valor devuelto

El número de subprocesos que se crearán en el módulo EXE.

### <a name="remarks"></a>Observaciones

Esta función estática calcula dinámicamente el número máximo de subprocesos para el módulo EXE, en función del número de procesadores. De forma predeterminada, este valor devuelto se pasa al método [Init](#init) para crear los subprocesos.

## <a name="ccomautothreadmoduleinit"></a><a name="init"></a>CComAutoThreadModule::Init

A partir de ATL `CComAutoThreadModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```

### <a name="parameters"></a>Parámetros

*P*<br/>
[en] Puntero a una matriz de entradas de mapa de objetos.

*H*<br/>
[en] La HINSTANCE `DLLMain` pasó `WinMain`a o .

*plibid*<br/>
[en] Puntero al LIBID de la biblioteca de tipos asociada al proyecto.

*nThreads*<br/>
[en] El número de subprocesos que se van a crear. De forma predeterminada, *nThreads* es el valor devuelto por [GetDefaultThreads](#getdefaultthreads).

### <a name="remarks"></a>Observaciones

Inicializa los miembros de datos y crea el número de subprocesos especificados por *nThreads*.

## <a name="ccomautothreadmodulelock"></a><a name="lock"></a>CComAutoThreadModule::Lock

A partir de ATL `CComAutoThreadModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
LONG Lock();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos o pruebas.

### <a name="remarks"></a>Observaciones

Realiza un incremento atómico en el recuento de bloqueos para el módulo y para el subproceso actual. `CComAutoThreadModule`utiliza el recuento de bloqueos de módulo para determinar si algún cliente está accediendo al módulo. El recuento de bloqueos en el subproceso actual se utiliza con fines estadísticos.

## <a name="ccomautothreadmodulem_allocator"></a><a name="m_allocator"></a>CComAutoThreadModule::m_Allocator

A partir de ATL `CComAutoThreadModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>Observaciones

El objeto que administra la selección de subprocesos. De forma `ThreadAllocator` predeterminada, el parámetro de plantilla de clase es [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

## <a name="ccomautothreadmodulem_nthreads"></a><a name="m_nthreads"></a>CComAutoThreadModule::m_nThreads

A partir de ATL `CComAutoThreadModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
int m_nThreads;
```

### <a name="remarks"></a>Observaciones

Contiene el número de subprocesos en el módulo EXE. Cuando se llama `m_nThreads` a [Init,](#init) se establece en el valor del parámetro *nThreads.* El apartamento asociado de cada subproceso se administra mediante un [CComApartment](../../atl/reference/ccomapartment-class.md) objeto.

## <a name="ccomautothreadmodulem_papartments"></a><a name="m_papartments"></a>CComAutoThreadModule::m_pApartments

A partir de ATL `CComAutoThreadModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>Observaciones

Apunta a una matriz de [CComApartment](../../atl/reference/ccomapartment-class.md) objetos, cada uno de los cuales administra un apartamento en el módulo. El número de elementos de la matriz se basa en el [m_nThreads](#m_nthreads) miembro.

## <a name="ccomautothreadmoduleunlock"></a><a name="unlock"></a>CComAutoThreadModule::Unlock

A partir de ATL `CComAutoThreadModule` 7.0, está obsoleto: consulte Clases de [módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
LONG Unlock();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos o pruebas.

### <a name="remarks"></a>Observaciones

Realiza una disminución atómica en el recuento de bloqueos para el módulo y para el subproceso actual. `CComAutoThreadModule`utiliza el recuento de bloqueos de módulo para determinar si algún cliente está accediendo al módulo. El recuento de bloqueos en el subproceso actual se utiliza con fines estadísticos.

Cuando el recuento de bloqueos del módulo llega a cero, el módulo se puede descargar.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clases de módulo](../../atl/atl-module-classes.md)
