---
title: IResourceManager (Estructura)
ms.date: 03/27/2019
f1_keywords:
- IResourceManager
- CONCRTRM/concurrency::IResourceManager
- CONCRTRM/concurrency::IResourceManager::IResourceManager::OSVersion
- CONCRTRM/concurrency::IResourceManager::IResourceManager::CreateNodeTopology
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetAvailableNodeCount
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetFirstNode
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Reference
- CONCRTRM/concurrency::IResourceManager::IResourceManager::RegisterScheduler
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Release
helpviewer_keywords:
- IResourceManager structure
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
ms.openlocfilehash: 15e27a586fc039791255c01a053f6a1109183f90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368185"
---
# <a name="iresourcemanager-structure"></a>IResourceManager (Estructura)

Una interfaz al Administrador de recursos del runtime de simultaneidad. Esta es la interfaz que usan los programadores para comunicares con el Administrador de recursos.

## <a name="syntax"></a>Sintaxis

```cpp
struct IResourceManager;
```

## <a name="members"></a>Miembros

### <a name="public-enumerations"></a>Enumeraciones públicas

|Nombre|Descripción|
|----------|-----------------|
|[IResourceManager::OSVersion](#osversion)|Un tipo enumerado que representa la versión del sistema operativo.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IResourceManager::CreateNodeTopology](#createnodetopology)|Presente solo en compilaciones de depuración del tiempo de ejecución, este método es un enlace de prueba diseñado para facilitar las pruebas de Resource Manager en topologías de hardware variables, sin necesidad de hardware real que coincida con la configuración. Con las compilaciones comerciales del tiempo de ejecución, este método se devolverá sin realizar ninguna acción.|
|[IResourceManager::GetAvailableNodeCount](#getavailablenodecount)|Devuelve el número de nodos disponibles para Resource Manager.|
|[IResourceManager::GetFirstNode](#getfirstnode)|Devuelve el primer nodo en orden de enumeración según lo definido por el Administrador de recursos.|
|[IResourceManager::Referencia](#reference)|Incrementa el recuento de referencias en la instancia de Resource Manager.|
|[IResourceManager::RegisterScheduler](#registerscheduler)|Registra un programador con Resource Manager. Una vez registrado el programador, debe comunicarse `ISchedulerProxy` con Resource Manager mediante la interfaz que se devuelve.|
|[IResourceManager::Liberar](#release)|Disminuye el recuento de referencias en la instancia de Resource Manager. Resource Manager se destruye cuando su `0`recuento de referencias va a .|

## <a name="remarks"></a>Observaciones

Utilice la función [CreateResourceManager](concurrency-namespace-functions.md) para obtener una interfaz para la instancia de singleton Resource Manager. El método incrementa un recuento de referencias en Resource Manager y debe invocar el método [IResourceManager::Release](#release) para liberar la referencia cuando haya terminado con Resource Manager. Normalmente, cada programador que cree invocará este método durante la creación y liberará la referencia al Administrador de recursos después de que se cierre.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IResourceManager`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

## <a name="iresourcemanagercreatenodetopology-method"></a><a name="createnodetopology"></a>Método IResourceManager::CreateNodeTopology

Presente solo en compilaciones de depuración del tiempo de ejecución, este método es un enlace de prueba diseñado para facilitar las pruebas de Resource Manager en topologías de hardware variables, sin necesidad de hardware real que coincida con la configuración. Con las compilaciones comerciales del tiempo de ejecución, este método se devolverá sin realizar ninguna acción.

```cpp
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```

### <a name="parameters"></a>Parámetros

*nodeCount*<br/>
El número de nodos de procesador que se simulan.

*pCoreCount*<br/>
Matriz que especifica el número de núcleos en cada nodo.

*pNodeDistance*<br/>
Matriz que especifica la distancia del nodo entre dos nodos cualquiera. Este parámetro puede `NULL`tener el valor .

*pProcessorGroups*<br/>
Matriz que especifica el grupo de procesadores al que pertenece cada nodo.

### <a name="remarks"></a>Observaciones

[invalid_argument](../../../standard-library/invalid-argument-class.md) se produce si `nodeCount` el `0` parámetro tiene el valor `pCoreCount` pasado o `NULL`si el parámetro tiene el valor .

[invalid_operation](invalid-operation-class.md) se produce si se llama a este método mientras existen otros programadores en el proceso.

## <a name="iresourcemanagergetavailablenodecount-method"></a><a name="getavailablenodecount"></a>Método IResourceManager::GetAvailableNodeCount

Devuelve el número de nodos disponibles para Resource Manager.

```cpp
virtual unsigned int GetAvailableNodeCount() const = 0;
```

### <a name="return-value"></a>Valor devuelto

El número de nodos disponibles para Resource Manager.

## <a name="iresourcemanagergetfirstnode-method"></a><a name="getfirstnode"></a>IResourceManager::GetFirstNode Método

Devuelve el primer nodo en orden de enumeración según lo definido por el Administrador de recursos.

```cpp
virtual ITopologyNode* GetFirstNode() const = 0;
```

### <a name="return-value"></a>Valor devuelto

El primer nodo en orden de enumeración definido por el Administrador de recursos.

## <a name="iresourcemanagerosversion-enumeration"></a><a name="osversion"></a>IResourceManager::OSVersion (enumeración)

Un tipo enumerado que representa la versión del sistema operativo.

```cpp
enum OSVersion;
```

## <a name="iresourcemanagerreference-method"></a><a name="reference"></a>IResourceManager::Método de referencia

Incrementa el recuento de referencias en la instancia de Resource Manager.

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>Valor devuelto

El recuento de referencias resultante.

## <a name="iresourcemanagerregisterscheduler-method"></a><a name="registerscheduler"></a>Método IResourceManager::RegisterScheduler

Registra un programador con Resource Manager. Una vez registrado el programador, debe comunicarse `ISchedulerProxy` con Resource Manager mediante la interfaz que se devuelve.

```cpp
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```

### <a name="parameters"></a>Parámetros

*pScheduler*<br/>
Una `IScheduler` interfaz para el programador que se va a registrar.

*version*<br/>
La versión de la interfaz de comunicación que utiliza el programador para comunicarse con Resource Manager. El uso de una versión permite que Resource Manager evolucione la interfaz de comunicación al tiempo que permite a los programadores obtener acceso a características anteriores. Los programadores que deseen usar las características de Resource Manager `CONCRT_RM_VERSION_1`presentes en Visual Studio 2010 deben usar la versión .

### <a name="return-value"></a>Valor devuelto

La `ISchedulerProxy` interfaz que Resource Manager ha asociado con el programador. El programador debe usar esta interfaz para comunicarse con Resource Manager a partir de este momento.

### <a name="remarks"></a>Observaciones

Utilice este método para iniciar la comunicación con Resource Manager. El método `IScheduler` asocia la interfaz `ISchedulerProxy` del programador con una interfaz y se la devuelve. Puede usar la interfaz devuelta para solicitar recursos de ejecución para su uso por el programador o para suscribirsubprocesos con Resource Manager. Resource Manager usará elementos de directiva de la directiva del programador devuelta por el método [IScheduler::GetPolicy](ischeduler-structure.md#getpolicy) para determinar qué tipo de subprocesos necesitará ejecutar el trabajo. Si `SchedulerKind` la clave de `UmsThreadDefault` directiva tiene el valor y el `UmsThreadDefault`valor `IScheduler` se vuelve a leer `IUMSScheduler` de la directiva como el valor, la interfaz pasada al método debe ser una interfaz.

El método produce `invalid_argument` una excepción si el parámetro `pScheduler` tiene el valor `NULL` o si el parámetro `version` no es una versión válida para la interfaz de comunicación.

## <a name="iresourcemanagerrelease-method"></a><a name="release"></a>Método IResourceManager::Release

Disminuye el recuento de referencias en la instancia de Resource Manager. Resource Manager se destruye cuando su `0`recuento de referencias va a .

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Valor devuelto

El recuento de referencias resultante.

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)<br/>
[ISchedulerProxy (estructura)](ischedulerproxy-structure.md)<br/>
[IScheduler (estructura)](ischeduler-structure.md)
