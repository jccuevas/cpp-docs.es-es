---
title: "CJumpList Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxadv/CJumpList"
  - "CJumpList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CJumpList class"
ms.assetid: d364d27e-f512-4b12-9872-c2a17c78ab1f
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# CJumpList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CJumpList` es la lista de métodos abreviados reveladora al hacer clic con el botón secundario en un icono en la barra de tareas.  
  
## Sintaxis  
  
```  
class CJumpList;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CJumpList::CJumpList](../Topic/CJumpList::CJumpList.md)|Crea un objeto `CJumpList`.|  
|[CJumpList::~CJumpList](../Topic/CJumpList::~CJumpList.md)|Destruye un objeto `CJumpList`.|  
  
|Name|Descripción|  
|----------|-----------------|  
|[CJumpList::AbortList](../Topic/CJumpList::AbortList.md)|Anula una transacción lista\-que compila sin confirmar.|  
|[CJumpList::AddDestination](../Topic/CJumpList::AddDestination.md)|Sobrecargado.  agrega el destino a la lista.|  
|[CJumpList::AddKnownCategory](../Topic/CJumpList::AddKnownCategory.md)|Anexa una categoría conocida a la lista.|  
|[CJumpList::AddTask](../Topic/CJumpList::AddTask.md)|Sobrecargado.  Agregar elementos a la categoría canónica de las tareas.|  
|[CJumpList::AddTasks](../Topic/CJumpList::AddTasks.md)|Agregar elementos a la categoría canónica de las tareas.|  
|[CJumpList::AddTaskSeparator](../Topic/CJumpList::AddTaskSeparator.md)|agrega un separador entre las tareas.|  
|[CJumpList::ClearAll](../Topic/CJumpList::ClearAll.md)|quita todas las tareas y destinos que se han agregado a la instancia actual de `CJumpList` hasta ahora.|  
|[CJumpList::ClearAllDestinations](../Topic/CJumpList::ClearAllDestinations.md)|quita todos los destinos que se han agregado a la instancia actual de `CJumpList` hasta ahora.|  
|[CJumpList::CommitList](../Topic/CJumpList::CommitList.md)|Finaliza una transacción lista\-que compila y confirma la lista designada en almacén asociado \(el registro en este caso\).|  
|[CJumpList::GetDestinationList](../Topic/CJumpList::GetDestinationList.md)|Recupera un puntero de interfaz a la lista de destinos.|  
|[CJumpList::GetMaxSlots](../Topic/CJumpList::GetMaxSlots.md)|Recupera el número máximo de elementos, incluidos los encabezados de la categoría que se pueden mostrar en el menú de destino de la aplicación de llamada.|  
|[CJumpList::GetRemovedItems](../Topic/CJumpList::GetRemovedItems.md)|Devuelve una matriz de elementos que representan destinos colocados.|  
|[CJumpList::InitializeList](../Topic/CJumpList::InitializeList.md)|Inicia una transacción el lista\-compilar.|  
|[CJumpList::SetAppID](../Topic/CJumpList::SetAppID.md)|Establece el identificador del Modelo de usuario de la aplicación para la lista que se compilará.|  
  
## Jerarquía de herencia  
 [CJumpList](../../mfc/reference/cjumplist-class.md)  
  
## Requisitos  
 **encabezado:** afxadv.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)