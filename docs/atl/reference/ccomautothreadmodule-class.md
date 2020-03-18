---
title: CComAutoThreadModule (clase)
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
ms.openlocfilehash: 9b0fa685bf9a7de94b158bd62b00161c1b58562d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423319"
---
# <a name="ccomautothreadmodule-class"></a>CComAutoThreadModule (clase)

A partir de ATL 7,0, `CComAutoThreadModule` está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class ThreadAllocator = CComSimpleThreadAllocator>
class CComAutoThreadModule : public CComModule
```

#### <a name="parameters"></a>Parámetros

*ThreadAllocator*<br/>
de La clase que administra la selección del subproceso. El valor predeterminado es [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[CreateInstance](#createinstance)|Selecciona un subproceso y, a continuación, crea un objeto en el contenedor asociado.|
|[GetDefaultThreads](#getdefaultthreads)|Estático Calcula dinámicamente el número de subprocesos para el módulo en función del número de procesadores.|
|[Init](#init)|Crea los subprocesos del módulo.|
|[Bloquear](#lock)|Incrementa el recuento de bloqueos en el módulo y en el subproceso actual.|
|[Pulsa](#unlock)|Disminuye el recuento de bloqueos en el módulo y en el subproceso actual.|

### <a name="data-members"></a>Miembros de datos

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[dwThreadID](#dwthreadid)|Contiene el identificador del subproceso actual.|
|[m_Allocator](#m_allocator)|Administra la selección del subproceso.|
|[m_nThreads](#m_nthreads)|Contiene el número de subprocesos del módulo.|
|[m_pApartments](#m_papartments)|Administra los apartamentos del módulo.|

## <a name="remarks"></a>Observaciones

> [!NOTE]
>  Esta clase está obsoleta, se ha reemplazado por las clases derivadas [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) y [CAtlModule](../../atl/reference/catlmodule-class.md) . La información siguiente es para su uso con versiones anteriores de ATL.

`CComAutoThreadModule` deriva de [CComModule](../../atl/reference/ccommodule-class.md) para implementar un servidor com de modelo de subprocesos, para los servicios exe y Windows. `CComAutoThreadModule` usa [CComApartment](../../atl/reference/ccomapartment-class.md) para administrar un apartamento para cada subproceso del módulo.

Derive el módulo de `CComAutoThreadModule` cuando desee crear objetos en varios apartamentos. También debe incluir la macro [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) en la definición de clase del objeto para especificar [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) como el generador de clases.

De forma predeterminada, ATL COM AppWizard (el Asistente para proyectos ATL en Visual Studio .NET) derivará el módulo de `CComModule`. Para usar `CComAutoThreadModule`, modifique la definición de clase. Por ejemplo:

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

**Encabezado:** ATLBase. h

##  <a name="createinstance"></a>CComAutoThreadModule:: CreateInstance

A partir de ATL 7,0, `CComAutoThreadModule` está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>Parámetros

*pfnCreateInstance*<br/>
de Puntero a una función de creador.

*riid*<br/>
de IID de la interfaz solicitada.

*ppvObj*<br/>
enuncia Puntero al puntero de interfaz identificado por *riid*. Si el objeto no admite esta interfaz, *ppvObj* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Selecciona un subproceso y, a continuación, crea un objeto en el contenedor asociado.

##  <a name="dwthreadid"></a>CComAutoThreadModule::d wThreadID

A partir de ATL 7,0, `CComAutoThreadModule` está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
DWORD dwThreadID;
```

### <a name="remarks"></a>Observaciones

Contiene el identificador del subproceso actual.

##  <a name="getdefaultthreads"></a>CComAutoThreadModule:: GetDefaultThreads

A partir de ATL 7,0, `CComAutoThreadModule` está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Valor devuelto

Número de subprocesos que se van a crear en el módulo EXE.

### <a name="remarks"></a>Observaciones

Esta función estática calcula dinámicamente el número máximo de subprocesos para el módulo EXE, en función del número de procesadores. De forma predeterminada, este valor devuelto se pasa al método [init](#init) para crear los subprocesos.

##  <a name="init"></a>CComAutoThreadModule:: init

A partir de ATL 7,0, `CComAutoThreadModule` está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```

### <a name="parameters"></a>Parámetros

*p*<br/>
de Puntero a una matriz de entradas de asignación de objetos.

*h*<br/>
de HINSTANCE pasado a `DLLMain` o `WinMain`.

*plibid*<br/>
de Puntero al LIBId de la biblioteca de tipos asociada al proyecto.

*nThreads*<br/>
de Número de subprocesos que se van a crear. De forma predeterminada, *nThreads* es el valor devuelto por [GetDefaultThreads](#getdefaultthreads).

### <a name="remarks"></a>Observaciones

Inicializa los miembros de datos y crea el número de subprocesos especificados por *nThreads*.

##  <a name="lock"></a>CComAutoThreadModule:: Lock

A partir de ATL 7,0, `CComAutoThreadModule` está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
LONG Lock();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos o pruebas.

### <a name="remarks"></a>Observaciones

Realiza un incremento atómico en el recuento de bloqueos del módulo y para el subproceso actual. `CComAutoThreadModule` usa el recuento de bloqueos del módulo para determinar si los clientes tienen acceso al módulo. El recuento de bloqueos en el subproceso actual se usa para fines estadísticos.

##  <a name="m_allocator"></a>CComAutoThreadModule:: m_Allocator

A partir de ATL 7,0, `CComAutoThreadModule` está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>Observaciones

Objeto que administra la selección del subproceso. De forma predeterminada, el parámetro de plantilla de clase `ThreadAllocator` es [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

##  <a name="m_nthreads"></a>CComAutoThreadModule:: m_nThreads

A partir de ATL 7,0, `CComAutoThreadModule` está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
int m_nThreads;
```

### <a name="remarks"></a>Observaciones

Contiene el número de subprocesos del módulo EXE. Cuando se llama a [init](#init) , `m_nThreads` se establece en el valor del parámetro *nThreads* . Un objeto [CComApartment](../../atl/reference/ccomapartment-class.md) administra cada apartamento asociado de cada subproceso.

##  <a name="m_papartments"></a>CComAutoThreadModule:: m_pApartments

A partir de ATL 7,0, `CComAutoThreadModule` está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>Observaciones

Apunta a una matriz de objetos [CComApartment](../../atl/reference/ccomapartment-class.md) , cada uno de los cuales administra un apartamento en el módulo. El número de elementos de la matriz se basa en el miembro de [m_nThreads](#m_nthreads) .

##  <a name="unlock"></a>CComAutoThreadModule:: Unlock

A partir de ATL 7,0, `CComAutoThreadModule` está obsoleto: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
LONG Unlock();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos o pruebas.

### <a name="remarks"></a>Observaciones

Realiza una reducción atómica en el recuento de bloqueos del módulo y para el subproceso actual. `CComAutoThreadModule` usa el recuento de bloqueos del módulo para determinar si los clientes tienen acceso al módulo. El recuento de bloqueos en el subproceso actual se usa para fines estadísticos.

Cuando el número de bloqueos del módulo llega a cero, se puede descargar el módulo.

## <a name="see-also"></a>Consulte también

[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[Clases de módulo](../../atl/atl-module-classes.md)
