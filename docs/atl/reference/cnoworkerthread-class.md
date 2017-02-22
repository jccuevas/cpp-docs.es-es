---
title: "CNoWorkerThread Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CNoWorkerThread"
  - "ATL.CNoWorkerThread"
  - "CNoWorkerThread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CNoWorkerThread class"
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CNoWorkerThread Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utilice esta clase como el argumento para que el parámetro de plantilla de `MonitorClass` almacene en caché clases si desea deshabilitar mantenimiento dinámico de caché.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CNoWorkerThread  
  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CNoWorkerThread::AddHandle](../Topic/CNoWorkerThread::AddHandle.md)|equivalente no funcional de [CWorkerThread:: AddHandle](../Topic/CWorkerThread::AddHandle.md).|  
|[CNoWorkerThread::AddTimer](../Topic/CNoWorkerThread::AddTimer.md)|equivalente no funcional de [CWorkerThread:: AddTimer](../Topic/CWorkerThread::AddTimer.md).|  
|[CNoWorkerThread::GetThreadHandle](../Topic/CNoWorkerThread::GetThreadHandle.md)|Equivalente no funcional de [CWorkerThread::GetThreadHandle](../Topic/CWorkerThread::GetThreadHandle.md).|  
|[CNoWorkerThread::GetThreadId](../Topic/CNoWorkerThread::GetThreadId.md)|Equivalente no funcional de [CWorkerThread::GetThreadId](../Topic/CWorkerThread::GetThreadId.md).|  
|[CNoWorkerThread::Initialize](../Topic/CNoWorkerThread::Initialize.md)|equivalente no funcional de [CWorkerThread:: Inicialice](../Topic/CWorkerThread::Initialize.md).|  
|[CNoWorkerThread::RemoveHandle](../Topic/CNoWorkerThread::RemoveHandle.md)|equivalente no funcional de [CWorkerThread:: RemoveHandle](../Topic/CWorkerThread::RemoveHandle.md).|  
|[CNoWorkerThread::Shutdown](../Topic/CNoWorkerThread::Shutdown.md)|equivalente no funcional de [CWorkerThread:: Apagado](../Topic/CWorkerThread::Shutdown.md).|  
  
## Comentarios  
 Esta clase proporciona la misma interfaz pública que [CWorkerThread](../../atl/reference/cworkerthread-class.md).  Se espera que esta interfaz es proporcionada por el parámetro de plantilla de `MonitorClass` a las clases de caché.  
  
 Los métodos de esta clase se implementan para no hacer nada.  Los métodos que devuelven un retorno S\_OK HRESULT siempre, y los métodos que devuelven un retorno 0 HANDLE o el identificador de subproceso siempre.  
  
## Requisitos  
 **encabezado:** atlutil.h