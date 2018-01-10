---
title: IResourceManager (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords: IResourceManager structure
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0a88cfafe9bbfdc04776050a0a956bf9a8b6766e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
|[IResourceManager:: OSVersion](#osversion)|Un tipo enumerado que representa la versión del sistema operativo.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IResourceManager:: CreateNodeTopology](#createnodetopology)|Presente únicamente en depuración compilaciones del runtime, este método es un enlace de prueba diseñado para facilitar la prueba del Administrador de recursos en diversas topologías de hardware, sin necesidad de hardware real coincide con la configuración. Con compilaciones del runtime, este método devolverá sin realizar ninguna acción.|  
|[IResourceManager:: Getavailablenodecount](#getavailablenodecount)|Devuelve el número de nodos disponibles para el Administrador de recursos.|  
|[IResourceManager:: Getfirstnode](#getfirstnode)|Devuelve el primer nodo en el orden de enumeración de acuerdo con el Administrador de recursos.|  
|[IResourceManager:: Reference](#reference)|Incrementa el recuento de referencias en la instancia del Administrador de recursos.|  
|[IResourceManager:: RegisterScheduler](#registerscheduler)|Registra a un programador con el Administrador de recursos. Una vez que el programador está registrado, debe comunicarse con el Administrador de recursos mediante el `ISchedulerProxy` interfaz que se devuelve.|  
|[IResourceManager:: Release](#release)|Disminuye el recuento de referencias en la instancia del Administrador de recursos. El Administrador de recursos se destruye cuando su recuento de referencias llega a `0`.|  
  
## <a name="remarks"></a>Comentarios  
 Use la [CreateResourceManager](concurrency-namespace-functions.md) función para obtener una interfaz a la instancia singleton del Administrador de recursos. El método incrementa un recuento de referencias en el Administrador de recursos y se debería invocar el [IResourceManager:: Release](#release) método para liberar la referencia cuando haya terminado con el Administrador de recursos. Normalmente, cada programador que crear invocar este método durante la creación y liberar la referencia al administrador de recursos después de se cierra.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IResourceManager`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="createnodetopology"></a>IResourceManager:: CreateNodeTopology (método)  
 Presente únicamente en depuración compilaciones del runtime, este método es un enlace de prueba diseñado para facilitar la prueba del Administrador de recursos en diversas topologías de hardware, sin necesidad de hardware real coincide con la configuración. Con compilaciones del runtime, este método devolverá sin realizar ninguna acción.  
  
```
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `nodeCount`  
 El número de nodos de procesador que se simulan.  
  
 `pCoreCount`  
 Una matriz que especifica el número de núcleos en cada nodo.  
  
 `pNodeDistance`  
 Una matriz que especifica la distancia de nodo entre dos nodos. Este parámetro puede tener el valor `NULL`.  
  
 `pProcessorGroups`  
 Una matriz que especifica el grupo de procesadores al que pertenece cada nodo.  
  
### <a name="remarks"></a>Comentarios  
 [invalid_argument](../../../standard-library/invalid-argument-class.md) se produce si el parámetro `nodeCount` tiene el valor `0` se pasó, o si el parámetro `pCoreCount` tiene el valor `NULL`.  
  
 [invalid_operation](invalid-operation-class.md) se produce si se llama a este método mientras otros programadores existen en el proceso.  
  
##  <a name="getavailablenodecount"></a>IResourceManager:: Getavailablenodecount (método)  
 Devuelve el número de nodos disponibles para el Administrador de recursos.  
  
```
virtual unsigned int GetAvailableNodeCount() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de nodos disponibles para el Administrador de recursos.  
  
##  <a name="getfirstnode"></a>IResourceManager:: Getfirstnode (método)  
 Devuelve el primer nodo en el orden de enumeración de acuerdo con el Administrador de recursos.  
  
```
virtual ITopologyNode* GetFirstNode() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El primer nodo en el orden de enumeración de acuerdo con el Administrador de recursos.  
  
##  <a name="iresourcemanager__osversion"></a>IResourceManager:: OSVersion (enumeración)  
 Un tipo enumerado que representa la versión del sistema operativo.  
  
```
enum OSVersion;
```  
  
##  <a name="reference"></a>IResourceManager:: Reference (método)  
 Incrementa el recuento de referencias en la instancia del Administrador de recursos.  
  
```
virtual unsigned int Reference() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El recuento de referencias resultante.  
  
##  <a name="registerscheduler"></a>IResourceManager:: RegisterScheduler (método)  
 Registra a un programador con el Administrador de recursos. Una vez que el programador está registrado, debe comunicarse con el Administrador de recursos mediante el `ISchedulerProxy` interfaz que se devuelve.  
  
```
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `pScheduler`  
 Un `IScheduler` interfaz al programador que se registrará.  
  
 `version`  
 La versión de interfaz de comunicación que el programador está usando para comunicarse con el Administrador de recursos. Usa una versión permite que el Administrador de recursos evolucione la interfaz de comunicación mientras que los programadores obtener acceso a características anteriores. Los programadores que deseen utilizar características del Administrador de recursos presentes en Visual Studio 2010 deben usar la versión `CONCRT_RM_VERSION_1`.  
  
### <a name="return-value"></a>Valor devuelto  
 El `ISchedulerProxy` interfaz el Administrador de recursos asociado a su programador. El programador debería usar esta interfaz para comunicarse con el Administrador de recursos desde este punto en.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para iniciar la comunicación con el Administrador de recursos. Asocia el método la `IScheduler` interfaz para el programador con una `ISchedulerProxy` interfaz y las manos que vuelva a cambiarlo a usted. Puede usar la interfaz devuelta para solicitar recursos de ejecución para su uso por el programador, o suscribir subprocesos con el Administrador de recursos. El Administrador de recursos usará los elementos de la directiva de la directiva del programador devuelta por la [IScheduler:: GetPolicy](ischeduler-structure.md#getpolicy) método para determinar qué tipo de subprocesos que el programador deberá ejecutar el trabajo. Si su `SchedulerKind` clave de directiva tiene el valor `UmsThreadDefault` y se lee el valor fuera de la directiva como el valor `UmsThreadDefault`, `IScheduler` pasada al método de interfaz debe ser un `IUMSScheduler` interfaz.  
  
 El método produce una `invalid_argument` excepción si el parámetro `pScheduler` tiene el valor `NULL` o si el parámetro `version` no es una versión no válida para la interfaz de comunicación.  
  
##  <a name="release"></a>IResourceManager:: Release (método)  
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
