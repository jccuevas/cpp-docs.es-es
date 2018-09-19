---
title: IResourceManager (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- IResourceManager structure
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d1032b2db7d1552beb40eb724b9953142b9b2ac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027419"
---
# <a name="iresourcemanager-structure"></a>IResourceManager (Estructura)
Una interfaz al Administrador de recursos del runtime de simultaneidad. Esta es la interfaz que usan los programadores para comunicares con el Administrador de recursos.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct IResourceManager;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-enumerations"></a>Enumeraciones públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[IResourceManager::OSVersion](#osversion)|Un tipo enumerado que representa la versión del sistema operativo.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IResourceManager::CreateNodeTopology](#createnodetopology)|Compilaciones de presente solo en modo de depuración del tiempo de ejecución, este método es un enlace de prueba diseñado para facilitar las pruebas del Administrador de recursos en diversas topologías de hardware, sin necesidad de hardware real coincide con la configuración. Con las compilaciones comerciales de tiempo de ejecución, este método devolverá sin realizar ninguna acción.|  
|[IResourceManager::GetAvailableNodeCount](#getavailablenodecount)|Devuelve el número de nodos disponibles para el Administrador de recursos.|  
|[IResourceManager::GetFirstNode](#getfirstnode)|Devuelve el primer nodo en el orden de enumeración como se define por el Administrador de recursos.|  
|[IResourceManager:: Reference](#reference)|Incrementa el recuento de referencias en la instancia del Administrador de recursos.|  
|[IResourceManager::RegisterScheduler](#registerscheduler)|Registra a un programador con el Administrador de recursos. Una vez que el programador está registrado, que debe comunicarse con el Administrador de recursos mediante el `ISchedulerProxy` interfaz que se devuelve.|  
|[IResourceManager:: Release](#release)|Disminuye el recuento de referencias en la instancia del Administrador de recursos. El Administrador de recursos se destruye cuando su recuento de referencias llega a `0`.|  
  
## <a name="remarks"></a>Comentarios  
 Use la [CreateResourceManager](concurrency-namespace-functions.md) función para obtener una interfaz a la instancia del Administrador de recursos de singleton. El método incrementa un recuento de referencias en el Administrador de recursos y se debería invocar el [IResourceManager:: Release](#release) método para liberar la referencia cuando haya terminado con el Administrador de recursos. Normalmente, cada programador que crea invocar este método durante la creación y liberar la referencia al administrador de recursos después de cerrarse.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IResourceManager`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="createnodetopology"></a>  CreateNodeTopology (método)  
 Compilaciones de presente solo en modo de depuración del tiempo de ejecución, este método es un enlace de prueba diseñado para facilitar las pruebas del Administrador de recursos en diversas topologías de hardware, sin necesidad de hardware real coincide con la configuración. Con las compilaciones comerciales de tiempo de ejecución, este método devolverá sin realizar ninguna acción.  
  
```
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
*nodeCount*<br/>
El número de nodos de procesador que se está simulando.  
  
*pCoreCount*<br/>
Una matriz que especifica el número de núcleos en cada nodo.  
  
*pNodeDistance*<br/>
Una matriz que especifica la distancia del nodo entre dos nodos. Este parámetro puede tener el valor `NULL`.  
  
*pProcessorGroups*<br/>
Una matriz que especifica el grupo de procesadores que pertenece cada nodo.  
  
### <a name="remarks"></a>Comentarios  
 [invalid_argument](../../../standard-library/invalid-argument-class.md) se produce si el parámetro `nodeCount` tiene el valor `0` pasado, o si el parámetro `pCoreCount` tiene el valor `NULL`.  
  
 [invalid_operation](invalid-operation-class.md) se produce si se llama a este método mientras otros programadores existen en el proceso.  
  
##  <a name="getavailablenodecount"></a>  Getavailablenodecount (método)  
 Devuelve el número de nodos disponibles para el Administrador de recursos.  
  
```
virtual unsigned int GetAvailableNodeCount() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de nodos disponibles para el Administrador de recursos.  
  
##  <a name="getfirstnode"></a>  Getfirstnode (método)  
 Devuelve el primer nodo en el orden de enumeración como se define por el Administrador de recursos.  
  
```
virtual ITopologyNode* GetFirstNode() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El primer nodo en el orden de enumeración como se define por el Administrador de recursos.  
  
##  <a name="iresourcemanager__osversion"></a>  IResourceManager:: OSVersion (enumeración)  
 Un tipo enumerado que representa la versión del sistema operativo.  
  
```
enum OSVersion;
```  
  
##  <a name="reference"></a>  IResourceManager:: Reference (método)  
 Incrementa el recuento de referencias en la instancia del Administrador de recursos.  
  
```
virtual unsigned int Reference() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El recuento de referencias resultante.  
  
##  <a name="registerscheduler"></a>  RegisterScheduler (método)  
 Registra a un programador con el Administrador de recursos. Una vez que el programador está registrado, que debe comunicarse con el Administrador de recursos mediante el `ISchedulerProxy` interfaz que se devuelve.  
  
```
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
*pScheduler*<br/>
Un `IScheduler` interfaz al programador que se registrarán.  
  
*version*<br/>
La versión de la interfaz de comunicación el programador usa para comunicarse con el Administrador de recursos. Usa una versión permite que el Administrador de recursos para desarrollar la interfaz de comunicación mientras que los programadores obtener acceso a características anteriores. Los programadores que deseen utilizar las características del Administrador de recursos presentes en Visual Studio 2010 deben usar la versión `CONCRT_RM_VERSION_1`.  
  
### <a name="return-value"></a>Valor devuelto  
 El `ISchedulerProxy` el Administrador de recursos está asociado con el programador de interfaz. El programador debe usar esta interfaz para comunicarse con el Administrador de recursos desde este punto en.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para iniciar la comunicación con el Administrador de recursos. El método asocia la `IScheduler` interfaz para el programador con un `ISchedulerProxy` interfaz y se la devuelve. Puede usar la interfaz devuelta para solicitar recursos de ejecución para su uso por su programador, o suscribirse subprocesos con el Administrador de recursos. El Administrador de recursos usará los elementos de directiva de la directiva de programador devuelto por la [IScheduler](ischeduler-structure.md#getpolicy) método para determinar qué tipo de subprocesos que el programador deberá ejecutar el trabajo. Si su `SchedulerKind` clave de la directiva tiene el valor `UmsThreadDefault` y se lee el valor fuera de la directiva como el valor `UmsThreadDefault`, el `IScheduler` pasada al método de interfaz debe ser un `IUMSScheduler` interfaz.  
  
 El método produce una `invalid_argument` excepción si el parámetro `pScheduler` tiene el valor `NULL` o si el parámetro `version` no es una versión válida para la interfaz de comunicación.  
  
##  <a name="release"></a>  IResourceManager:: Release (método)  
 Disminuye el recuento de referencias en la instancia del Administrador de recursos. El Administrador de recursos se destruye cuando su recuento de referencias llega a `0`.  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El recuento de referencias resultante.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [ISchedulerProxy (estructura)](ischedulerproxy-structure.md)   
 [IScheduler (estructura)](ischeduler-structure.md)
