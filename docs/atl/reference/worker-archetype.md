---
title: Arquetipo de trabajo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
caps.latest.revision: 16
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 046160644cca3bd23e4293a3c52692d2b4c94cd5
ms.lasthandoff: 02/24/2017

---
# <a name="worker-archetype"></a>Arquetipo de trabajo
Las clases que se ajusten a la *trabajo* Arquetipo de proporcionar el código para procesar elementos de trabajo en cola en un grupo de subprocesos.  
  
 **Implementación**  
  
 Para implementar una clase que se ajuste a esta Arquetipo, la clase debe proporcionar las siguientes características:  
  
|Método|Descripción|  
|------------|-----------------|  
|[Inicializar](#initialize)|Se llama para inicializar el objeto de trabajo antes de pasan las solicitudes [Execute](#execute).|  
|[Ejecutar](#execute)|Se llama para procesar un elemento de trabajo.|  
|[Finalizar](#terminate)|Llamado para cancelar la inicialización del objeto de trabajo después de que todas las solicitudes se han pasado a [Execute](#execute).|  
  
|Definición de tipo|Descripción|  
|-------------|-----------------|  
|[RequestType](#requesttype)|Definición de tipos para el tipo de elemento de trabajo que puede ser procesado por la clase de trabajo.|  
  
 Una típica *trabajo* clase tiene el siguiente aspecto:  
  
 [!code-cpp[NVC_ATL_Utilities&#137;](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]  
  
 **Implementaciones existentes**  
  
 Estas clases se ajustan a este Arquetipo:  
  
|Clase|Descripción|  
|-----------|-----------------|  
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|Recibe solicitudes del grupo de subprocesos y pasa un objeto de trabajo que se crea y se destruye para cada solicitud.|  
  
 **Uso**  
  
 Estos parámetros de plantilla esperar que la clase que se ajuste a esta Arquetipo:  
  
|Nombre del parámetro|Utilizada por|  
|--------------------|-------------|  
|*Trabajo*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|  
|*Trabajo*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlutil.h  
  
## <a name="a-nameexecuteaworkerarchetypeexecute"></a><a name="execute"></a>WorkerArchetype::Execute
Se llama para procesar un elemento de trabajo.  
  
  
  
```  
void Execute(
    RequestType request,  
    void* pvWorkerParam,  
    OVERLAPPED* pOverlapped);
```  
  
#### <a name="parameters"></a>Parámetros  
 `request`  
 El elemento de trabajo que se va a procesar. El elemento de trabajo es del mismo tipo como `RequestType`.  
  
 `pvWorkerParam`  
 Un parámetro personalizado que entiende la clase de trabajo. También pasa a `WorkerArchetype::Initialize` y `Terminate`.  
  
 `pOverlapped`  
 Un puntero a la [OVERLAPPED](http://msdn.microsoft.com/library/windows/desktop/ms684342) estructura utilizada para crear la cola de qué elementos se pusieron en cola.  
  
## <a name="a-nameinitializea-workerarchetypeinitialize"></a><a name="initialize"></a>WorkerArchetype::Initialize
Se llama para inicializar el objeto de trabajo antes de pasan las solicitudes `WorkerArchetype::Execute`.  
```
BOOL Initialize(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>Parámetros  
 `pvParam`  
 Un parámetro personalizado que entiende la clase de trabajo. También pasa a `WorkerArchetype::Terminate` y `WorkerArchetype::Execute`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devolver **TRUE** correctamente, **FALSE** en caso de error.  
  
## <a name="a-namerequesttypea-workerarchetyperequesttype"></a><a name="requesttype"></a>WorkerArchetype::RequestType
Definición de tipos para el tipo de elemento de trabajo que puede ser procesado por la clase de trabajo.  
  
```  
typedef MyRequestType RequestType;    
```  
  
### <a name="remarks"></a>Comentarios  
 Este tipo debe usarse como primer parámetro de `WorkerArchetype::Execute` y debe ser capaz de que se va a convertir a y desde un ULONG_PTR.  
  
## <a name="a-nameterminatea-workerarchetypeterminate"></a><a name="terminate"></a>WorkerArchetype::Terminate
Llamado para cancelar la inicialización del objeto de trabajo después de que todas las solicitudes se han pasado a `WorkerArchetype::Execute`).  
    
``` 
void Terminate(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>Parámetros  
 `pvParam`  
 Un parámetro personalizado que entiende la clase de trabajo. También pasa a `WorkerArchetype::Initialize` y `WorkerArchetype::Execute`.  
  
## <a name="see-also"></a>Vea también  
 [Arquetipos](../../atl/reference/atl-archetypes.md)   
 [Conceptos](../../atl/active-template-library-atl-concepts.md)   
 [Componentes de escritorio de COM de ATL](../../atl/atl-com-desktop-components.md)




