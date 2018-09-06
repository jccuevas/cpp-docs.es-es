---
title: CComAutoThreadModule (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CComAutoThreadModule class
- apartment model modules
ms.assetid: 13063ea5-a57e-4aac-97d3-227137262811
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0934a3c6690b75ffa2eca18f1fd38662bc2a9fd9
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43756995"
---
# <a name="ccomautothreadmodule-class"></a>CComAutoThreadModule (clase)

A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <class ThreadAllocator = CComSimpleThreadAllocator>  
class CComAutoThreadModule : public CComModule
```

#### <a name="parameters"></a>Parámetros

`ThreadAllocator`  
[in] La clase de administración de selección de subprocesos. El valor predeterminado es [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[CreateInstance](#createinstance)|Selecciona un subproceso y, a continuación, crea un objeto en el contenedor asociado.|
|[GetDefaultThreads](#getdefaultthreads)|(Estático) Calcula dinámicamente el número de subprocesos para el módulo en función del número de procesadores.|
|[Init](#init)|Crea subprocesos del módulo.|
|[Bloqueo](#lock)|Incrementa el recuento de bloqueos en el módulo y en el subproceso actual.|
|[Desbloquear](#unlock)|Disminuye el recuento de bloqueos en el módulo y en el subproceso actual.|

### <a name="data-members"></a>Miembros de datos

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[dwThreadID](#dwthreadid)|Contiene el identificador del subproceso actual.|
|[m_Allocator](#m_allocator)|Administra la selección de subprocesos.|
|[m_nThreads](#m_nthreads)|Contiene el número de subprocesos en el módulo.|
|[m_pApartments](#m_papartments)|Administra los apartamentos del módulo.|

## <a name="remarks"></a>Comentarios

> [!NOTE]
>  Esta clase está obsoleta, que se han reemplazado por la [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) y [CAtlModule](../../atl/reference/catlmodule-class.md) las clases derivadas. La siguiente información es para su uso con las versiones anteriores de ATL.

`CComAutoThreadModule` se deriva de [CComModule](../../atl/reference/ccommodule-class.md) para implementar un servidor COM de subprocesamiento de modelo, agrupadas por subproceso para los servicios de archivos exe y Windows. `CComAutoThreadModule` usa [CComApartment](../../atl/reference/ccomapartment-class.md) para administrar un contenedor para cada subproceso en el módulo.

Derivar del módulo desde `CComAutoThreadModule` cuando desee crear objetos en varios contenedores. También debe incluir el [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) macro en la definición de clase del objeto para especificar [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) como el generador de clases.

De forma predeterminada, el Asistente para aplicaciones de COM de ATL (el Asistente para proyectos ATL de Visual Studio. NET) se derivará del módulo desde `CComModule`. Para usar `CComAutoThreadModule`, modifique la definición de clase. Por ejemplo:

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

##  <a name="createinstance"></a>  CComAutoThreadModule::CreateInstance

A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>Parámetros

*pfnCreateInstance*  
[in] Un puntero a una función de creador.

*riid*  
[in] IID de la interfaz solicitada.

*ppvObj*  
[out] Un puntero al puntero de interfaz identificado por *riid*. Si el objeto no admite esta interfaz, *ppvObj* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Selecciona un subproceso y, a continuación, crea un objeto en el contenedor asociado.

##  <a name="dwthreadid"></a>  CComAutoThreadModule::dwThreadID

A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
DWORD dwThreadID;
```

### <a name="remarks"></a>Comentarios

Contiene el identificador del subproceso actual.

##  <a name="getdefaultthreads"></a>  CComAutoThreadModule::GetDefaultThreads

A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Valor devuelto

El número de subprocesos que se creará en el módulo del archivo EXE.

### <a name="remarks"></a>Comentarios

Esta función estática calcula dinámicamente el número máximo de subprocesos para el módulo ejecutable, en función del número de procesadores. De forma predeterminada, este valor devuelto se pasa a la [Init](#init) método para crear los subprocesos.

##  <a name="init"></a>  CComAutoThreadModule::Init

A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```

### <a name="parameters"></a>Parámetros

*p*  
[in] Un puntero a una matriz de entradas de asignación de objeto.

*h*  
[in] HINSTANCE pasa a `DLLMain` o `WinMain`.

*plibid*  
[in] Un puntero a LIBID de la biblioteca de tipos asociado al proyecto.

*nThreads*  
[in] El número de subprocesos que se va a crear. De forma predeterminada, *nThreads* es el valor devuelto por [GetDefaultThreads](#getdefaultthreads).

### <a name="remarks"></a>Comentarios

Inicializa los miembros de datos y crea el número de subprocesos especificado por *nThreads*.

##  <a name="lock"></a>  CComAutoThreadModule::Lock

A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
LONG Lock();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para el diagnóstico o de pruebas.

### <a name="remarks"></a>Comentarios

Realiza un incremento atómico en el recuento de bloqueos del módulo y para el subproceso actual. `CComAutoThreadModule` el recuento de bloqueos del módulo se usa para determinar si los clientes tienen acceso a los del módulo. El recuento de bloqueos en el subproceso actual se utiliza para fines estadísticos.

##  <a name="m_allocator"></a>  CComAutoThreadModule::m_Allocator

A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>Comentarios

El objeto de administración de selección de subprocesos. De forma predeterminada, el `ThreadAllocator` es el parámetro de plantilla de clase [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

##  <a name="m_nthreads"></a>  CComAutoThreadModule::m_nThreads

A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
int m_nThreads;
```

### <a name="remarks"></a>Comentarios

Contiene el número de subprocesos en el módulo del archivo EXE. Cuando [Init](#init) se llama, `m_nThreads` está establecido en el *nThreads* el valor del parámetro. Asociado de subprocesamiento cada estado administrado por un [CComApartment](../../atl/reference/ccomapartment-class.md) objeto.

##  <a name="m_papartments"></a>  CComAutoThreadModule::m_pApartments

A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>Comentarios

Señala a una matriz de [CComApartment](../../atl/reference/ccomapartment-class.md) objetos, cada uno de los cuales administra un apartamento en el módulo. El número de elementos de la matriz se basa en el [m_nThreads](#m_nthreads) miembro.

##  <a name="unlock"></a>  CComAutoThreadModule::Unlock

A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.

```
LONG Unlock();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para el diagnóstico o de pruebas.

### <a name="remarks"></a>Comentarios

Realiza un decremento atómico en el recuento de bloqueos del módulo y para el subproceso actual. `CComAutoThreadModule` el recuento de bloqueos del módulo se usa para determinar si los clientes tienen acceso a los del módulo. El recuento de bloqueos en el subproceso actual se utiliza para fines estadísticos.

Cuando el recuento de bloqueos del módulo llega a cero, se puede descargar el módulo.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)   
[Clases de módulo](../../atl/atl-module-classes.md)
