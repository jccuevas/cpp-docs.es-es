---
title: IResourceManager (estructura)
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
ms.openlocfilehash: 7ce5b07f5eb4272db1b00b7f0105b790ddbb28fe
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142984"
---
# <a name="iresourcemanager-structure"></a>IResourceManager (estructura)

Una interfaz al Administrador de recursos del runtime de simultaneidad. Esta es la interfaz que usan los programadores para comunicares con el Administrador de recursos.

## <a name="syntax"></a>Sintaxis

```cpp
struct IResourceManager;
```

## <a name="members"></a>Members

### <a name="public-enumerations"></a>Enumeraciones públicas

|Nombre|Descripción|
|----------|-----------------|
|[IResourceManager:: OSVersion](#osversion)|Un tipo enumerado que representa la versión del sistema operativo.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IResourceManager:: CreateNodeTopology (](#createnodetopology)|Presente únicamente en las compilaciones de depuración del tiempo de ejecución, este método es un enlace de prueba diseñado para facilitar la realización de pruebas de la Administrador de recursos en distintas topologías de hardware, sin necesidad de que el hardware real coincida con la configuración. Con las compilaciones comerciales del tiempo de ejecución, este método devolverá sin realizar ninguna acción.|
|[IResourceManager:: Getavailablenodecount (](#getavailablenodecount)|Devuelve el número de nodos disponibles para el Administrador de recursos.|
|[IResourceManager:: Getfirstnode (](#getfirstnode)|Devuelve el primer nodo en el orden de enumeración tal y como se define en el Administrador de recursos.|
|[IResourceManager:: Reference](#reference)|Incrementa el recuento de referencias en la instancia de Administrador de recursos.|
|[IResourceManager:: RegisterScheduler (](#registerscheduler)|Registra un programador con el Administrador de recursos. Una vez registrado el programador, debe comunicarse con el Administrador de recursos mediante la interfaz `ISchedulerProxy` que se devuelve.|
|[IResourceManager:: Release](#release)|Disminuye el recuento de referencias en la instancia de Administrador de recursos. El Administrador de recursos se destruye cuando su recuento de referencias va a `0`.|

## <a name="remarks"></a>Observaciones

Utilice la función [CreateResourceManager (](concurrency-namespace-functions.md) para obtener una interfaz para la instancia de administrador de recursos singleton. El método incrementa un recuento de referencias en el Administrador de recursos y debe invocar el método [IResourceManager:: Release](#release) para liberar la referencia cuando haya terminado con administrador de recursos. Normalmente, cada programador que se crea invocará este método durante la creación y liberará la referencia a la Administrador de recursos después de cerrarse.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IResourceManager`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm. h

**Espacio de nombres:** simultaneidad

## <a name="createnodetopology"></a>IResourceManager:: CreateNodeTopology ((método)

Presente únicamente en las compilaciones de depuración del tiempo de ejecución, este método es un enlace de prueba diseñado para facilitar la realización de pruebas de la Administrador de recursos en distintas topologías de hardware, sin necesidad de que el hardware real coincida con la configuración. Con las compilaciones comerciales del tiempo de ejecución, este método devolverá sin realizar ninguna acción.

```cpp
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```

### <a name="parameters"></a>Parámetros

*nodeCount*<br/>
El número de nodos del procesador que se simulan.

*pCoreCount*<br/>
Matriz que especifica el número de núcleos de cada nodo.

*pNodeDistance*<br/>
Una matriz que especifica la distancia del nodo entre dos nodos cualesquiera. Este parámetro puede tener el valor `NULL`.

*pProcessorGroups*<br/>
Matriz que especifica el grupo de procesadores al que pertenece cada nodo.

### <a name="remarks"></a>Observaciones

[invalid_argument](../../../standard-library/invalid-argument-class.md) se produce si el parámetro `nodeCount` tiene el valor `0` se ha pasado, o si el parámetro `pCoreCount` tiene el valor `NULL`.

[invalid_operation](invalid-operation-class.md) se produce si se llama a este método mientras existen otros programadores en el proceso.

## <a name="getavailablenodecount"></a>IResourceManager:: Getavailablenodecount ((método)

Devuelve el número de nodos disponibles para el Administrador de recursos.

```cpp
virtual unsigned int GetAvailableNodeCount() const = 0;
```

### <a name="return-value"></a>Valor devuelto

El número de nodos disponibles para el Administrador de recursos.

## <a name="getfirstnode"></a>IResourceManager:: Getfirstnode ((método)

Devuelve el primer nodo en el orden de enumeración tal y como se define en el Administrador de recursos.

```cpp
virtual ITopologyNode* GetFirstNode() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Primer nodo en el orden de enumeración tal y como se define en el Administrador de recursos.

## <a name="osversion"></a>IResourceManager:: OSVersion (enumeración)

Un tipo enumerado que representa la versión del sistema operativo.

```cpp
enum OSVersion;
```

## <a name="reference"></a>IResourceManager:: Reference (método)

Incrementa el recuento de referencias en la instancia de Administrador de recursos.

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>Valor devuelto

Recuento de referencias resultante.

## <a name="registerscheduler"></a>IResourceManager:: RegisterScheduler ((método)

Registra un programador con el Administrador de recursos. Una vez registrado el programador, debe comunicarse con el Administrador de recursos mediante la interfaz `ISchedulerProxy` que se devuelve.

```cpp
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```

### <a name="parameters"></a>Parámetros

*pScheduler*<br/>
Interfaz `IScheduler` al programador que se va a registrar.

*version*<br/>
La versión de la interfaz de comunicación que el programador usa para comunicarse con el Administrador de recursos. El uso de una versión permite que el Administrador de recursos evolucione la interfaz de comunicación, a la vez que permite a los programadores obtener acceso a las características anteriores. Los programadores que deseen usar Administrador de recursos características presentes en Visual Studio 2010 deben usar la versión `CONCRT_RM_VERSION_1`.

### <a name="return-value"></a>Valor devuelto

La interfaz de `ISchedulerProxy` que el Administrador de recursos tiene asociado al programador. El programador debe utilizar esta interfaz para comunicarse con Administrador de recursos a partir de este punto.

### <a name="remarks"></a>Observaciones

Utilice este método para iniciar la comunicación con el Administrador de recursos. El método asocia la interfaz de `IScheduler` para su programador con una interfaz `ISchedulerProxy` y la entrega a usted. Puede usar la interfaz devuelta para solicitar recursos de ejecución para su uso por parte de Scheduler o para suscribir subprocesos con el Administrador de recursos. El Administrador de recursos usará los elementos de directiva de la Directiva de Scheduler devuelta por el método [IScheduler:: GetPolicy](ischeduler-structure.md#getpolicy) para determinar qué tipo de subprocesos necesitará ejecutar el programador para ejecutar el trabajo. Si la clave de directiva de `SchedulerKind` tiene el valor `UmsThreadDefault` y se lee de nuevo el valor de la Directiva como `UmsThreadDefault`de valor, la interfaz de `IScheduler` que se pasa al método debe ser una interfaz `IUMSScheduler`.

El método produce una excepción `invalid_argument` si el `pScheduler` del parámetro tiene el valor `NULL` o si el parámetro `version` no es una versión válida para la interfaz de comunicación.

## <a name="release"></a>IResourceManager:: Release (método)

Disminuye el recuento de referencias en la instancia de Administrador de recursos. El Administrador de recursos se destruye cuando su recuento de referencias va a `0`.

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Valor devuelto

Recuento de referencias resultante.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[ISchedulerProxy (estructura)](ischedulerproxy-structure.md)<br/>
[IScheduler (estructura)](ischeduler-structure.md)
