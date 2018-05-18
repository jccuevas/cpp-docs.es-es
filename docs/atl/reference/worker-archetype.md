---
title: Trabajo Arquetipo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cee9df0b137655fe66e68c189de756f15233a94d
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="worker-archetype"></a>Arquetipo de trabajo
Las clases que se ajustan a la *trabajo* Arquetipo proporcionar el código para procesar elementos de trabajo en cola en un grupo de subprocesos.  
  
 **Implementación**  
  
 Para implementar una clase conforme a este Arquetipo, la clase debe proporcionar las siguientes características:  
  
|Método|Descripción|  
|------------|-----------------|  
|[Initialize](#initialize)|Se llama para inicializar el objeto de trabajo antes de que las solicitudes se pasan a [Execute](#execute).|  
|[Ejecutar](#execute)|Se llama para procesar un elemento de trabajo.|  
|[Finalizar](#terminate)|Llamado para cancelar la inicialización del objeto de trabajo después de que se han pasado todas las solicitudes al [Execute](#execute).|  
  
|Definición de tipo|Descripción|  
|-------------|-----------------|  
|[RequestType](#requesttype)|Una definición de tipo para el tipo de elemento de trabajo que puede ser procesado por la clase de trabajo.|  
  
 Una típica *trabajo* clase tiene el siguiente aspecto:  
  
 [!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]  
  
 **Implementaciones existentes**  
  
 Estas clases se ajustan a este Arquetipo:  
  
|Clase|Descripción|  
|-----------|-----------------|  
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|Recibe las solicitudes del grupo de subprocesos y los pasa a un objeto de trabajo que se crea y destruye para cada solicitud.|  
  
 **Uso**  
  
 Estos parámetros de plantilla esperar que la clase para que coincida con este Arquetipo:  
  
|Nombre de parámetro|Utilizada por|  
|--------------------|-------------|  
|*Trabajo*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|  
|*Trabajo*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlutil.h  
  
## <a name="execute"></a>WorkerArchetype::Execute
Se llama para procesar un elemento de trabajo.  
  
  
  
```  
void Execute(
    RequestType request,  
    void* pvWorkerParam,  
    OVERLAPPED* pOverlapped);
```  
  
#### <a name="parameters"></a>Parámetros  
 `request`  
 El elemento de trabajo para procesarse. El elemento de trabajo es del mismo tipo que `RequestType`.  
  
 `pvWorkerParam`  
 Un parámetro personalizado que se entiende por la clase de trabajo. También pasa a `WorkerArchetype::Initialize` y `Terminate`.  
  
 `pOverlapped`  
 Un puntero a la [OVERLAPPED](http://msdn.microsoft.com/library/windows/desktop/ms684342) estructura que se utiliza para crear la cola en qué trabajo se pusieron en cola los elementos.  
  
## <a name="initialize"></a> WorkerArchetype::Initialize
Se llama para inicializar el objeto de trabajo antes de que las solicitudes se pasan a `WorkerArchetype::Execute`.  
```
BOOL Initialize(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>Parámetros  
 `pvParam`  
 Un parámetro personalizado que se entiende por la clase de trabajo. También pasa a `WorkerArchetype::Terminate` y `WorkerArchetype::Execute`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devolver **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
## <a name="requesttype"></a> WorkerArchetype::RequestType
Una definición de tipo para el tipo de elemento de trabajo que puede ser procesado por la clase de trabajo.  
  
```  
typedef MyRequestType RequestType;    
```  
  
### <a name="remarks"></a>Comentarios  
 Este tipo debe usarse como el primer parámetro de `WorkerArchetype::Execute` y debe ser capaz de que se va a convertir a y desde un ULONG_PTR.  
  
## <a name="terminate"></a> WorkerArchetype::Terminate
Llamado para cancelar la inicialización del objeto de trabajo después de que se han pasado todas las solicitudes al `WorkerArchetype::Execute`).  
    
``` 
void Terminate(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>Parámetros  
 `pvParam`  
 Un parámetro personalizado que se entiende por la clase de trabajo. También pasa a `WorkerArchetype::Initialize` y `WorkerArchetype::Execute`.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../../atl/active-template-library-atl-concepts.md)   
 [Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md)



