---
title: IResourceManager (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
dev_langs:
- C++
helpviewer_keywords:
- IResourceManager structure
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 2d054bd632db90708d90fe8d791965b47f713493
ms.contentlocale: es-es
ms.lasthandoff: 03/17/2017

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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IResourceManager:: CreateNodeTopology](#createnodetopology)|Presente únicamente en depuración compilaciones del runtime, este método es un enlace de pruebas diseñado para facilitar las pruebas del Administrador de recursos en diversas topologías de hardware, sin necesidad de que coinciden con la configuración de hardware real. Con compilaciones del runtime, este método devolverá sin realizar ninguna acción.|  
|[IResourceManager:: Getavailablenodecount](#getavailablenodecount)|Devuelve el número de nodos disponibles en el Administrador de recursos.|  
|[IResourceManager:: Getfirstnode](#getfirstnode)|Devuelve el primer nodo en el orden de enumeración definido por el Administrador de recursos.|  
|[IResourceManager:: Reference](#reference)|Incrementa el recuento de referencias en la instancia del Administrador de recursos.|  
|[IResourceManager:: RegisterScheduler](#registerscheduler)|Registra a un programador con el Administrador de recursos. Una vez registrado el programador, debería comunicar con el Administrador de recursos mediante el `ISchedulerProxy` interfaz que se devuelve.|  
|[IResourceManager:: Release](#release)|Disminuye el recuento de referencias en la instancia del Administrador de recursos. El Administrador de recursos se destruye cuando su recuento de referencias llega a `0`.|  
  
## <a name="remarks"></a>Comentarios  
 Utilice la [CreateResourceManager](concurrency-namespace-functions.md) función para obtener una interfaz a la instancia singleton del Administrador de recursos. El método incrementa un recuento de referencias en el Administrador de recursos y se debería invocar el [IResourceManager:: Release](#release) método para liberar la referencia cuando haya terminado con el Administrador de recursos. Normalmente, cada programador que se crea invocará este método durante la creación y liberar la referencia al administrador de recursos después de cerrarse.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IResourceManager`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="createnodetopology"></a>IResourceManager:: CreateNodeTopology (método)  
 Presente únicamente en depuración compilaciones del runtime, este método es un enlace de pruebas diseñado para facilitar las pruebas del Administrador de recursos en diversas topologías de hardware, sin necesidad de que coinciden con la configuración de hardware real. Con compilaciones del runtime, este método devolverá sin realizar ninguna acción.  
  
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
 Matriz que especifica el número de núcleos de cada nodo.  
  
 `pNodeDistance`  
 Una matriz que especifica la distancia de nodo entre dos nodos. Este parámetro puede tener el valor `NULL`.  
  
 `pProcessorGroups`  
 Una matriz que especifica el grupo de procesadores al que pertenece cada nodo.  
  
### <a name="remarks"></a>Comentarios  
 [invalid_argument](../../../standard-library/invalid-argument-class.md) se produce si el parámetro `nodeCount` tiene el valor `0` pasado, o si el parámetro `pCoreCount` tiene el valor `NULL`.  
  
 [invalid_operation](invalid-operation-class.md) se produce si se llama a este método mientras otros programadores existen en el proceso.  
  
##  <a name="getavailablenodecount"></a>IResourceManager:: Getavailablenodecount (método)  
 Devuelve el número de nodos disponibles en el Administrador de recursos.  
  
```
virtual unsigned int GetAvailableNodeCount() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de nodos disponibles en el Administrador de recursos.  
  
##  <a name="getfirstnode"></a>IResourceManager:: Getfirstnode (método)  
 Devuelve el primer nodo en el orden de enumeración definido por el Administrador de recursos.  
  
```
virtual ITopologyNode* GetFirstNode() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El primer nodo en el orden de enumeración definido por el Administrador de recursos.  
  
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
 El recuento de referencia resultante.  
  
##  <a name="registerscheduler"></a>IResourceManager:: RegisterScheduler (método)  
 Registra a un programador con el Administrador de recursos. Una vez registrado el programador, debería comunicar con el Administrador de recursos mediante el `ISchedulerProxy` interfaz que se devuelve.  
  
```
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `pScheduler`  
 Un `IScheduler` interfaz al programador que se registrará.  
  
 `version`  
 La versión de la interfaz de comunicación que el programador está utilizando para comunicarse con el Administrador de recursos. Utilizar una versión permite que el Administrador de recursos evolucione la interfaz de comunicación mientras que los programadores pueden obtener acceso a características anteriores. Los programadores que deseen utilizar las funciones de administrador de recursos presentes en Visual Studio 2010 deben usar la versión `CONCRT_RM_VERSION_1`.  
  
### <a name="return-value"></a>Valor devuelto  
 El `ISchedulerProxy` el Administrador de recursos asociado a su programador de interfaz. El programador debería usar esta interfaz para comunicarse con el Administrador de recursos desde este punto en.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para iniciar la comunicación con el Administrador de recursos. El método asocia la `IScheduler` interfaz para el programador con una `ISchedulerProxy` interfaz y se la devuelve. Puede usar la interfaz devuelta para solicitar recursos de ejecución para que use su programador, o suscribir subprocesos con el Administrador de recursos. El Administrador de recursos usará los elementos de directiva desde la directiva del programador devuelta por la [IScheduler:: GetPolicy](ischeduler-structure.md#getpolicy) método para determinar qué tipo de subprocesos que el programador deberá ejecutar el trabajo. Si su `SchedulerKind` clave de directiva tiene el valor `UmsThreadDefault` y el valor se lee fuera de la directiva como el valor `UmsThreadDefault`, `IScheduler` pasada al método de interfaz debe ser un `IUMSScheduler` interfaz.  
  
 El método produce una `invalid_argument` excepción si el parámetro `pScheduler` tiene el valor `NULL` o si el parámetro `version` no es una versión válida para la interfaz de comunicación.  
  
##  <a name="release"></a>IResourceManager:: Release (método)  
 Disminuye el recuento de referencias en la instancia del Administrador de recursos. El Administrador de recursos se destruye cuando su recuento de referencias llega a `0`.  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El recuento de referencia resultante.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [ISchedulerProxy (estructura)](ischedulerproxy-structure.md)   
 [IScheduler (estructura)](ischeduler-structure.md)

