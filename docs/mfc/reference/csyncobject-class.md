---
title: "CSyncObject Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSyncObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSyncObject class"
  - "clases de sincronización, CSyncObject"
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSyncObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una clase virtual pura que proporciona funcionalidad común a los objetos de sincronización en Win32.  
  
## Sintaxis  
  
```  
class CSyncObject : public CObject  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSyncObject::CSyncObject](../Topic/CSyncObject::CSyncObject.md)|Crea un objeto `CSyncObject`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSyncObject::Lock](../Topic/CSyncObject::Lock.md)|Obtener acceso al objeto de sincronización.|  
|[CSyncObject::Unlock](../Topic/CSyncObject::Unlock.md)|Obtener acceso al objeto de sincronización.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSyncObject::operator HANDLE](../Topic/CSyncObject::operator%20HANDLE.md)|Proporciona acceso al objeto de sincronización.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSyncObject::m\_hObject](../Topic/CSyncObject::m_hObject.md)|El identificador del objeto de sincronización subyacente.|  
  
## Comentarios  
 La biblioteca Microsoft Foundation Class proporciona varias clases derivadas de `CSyncObject`.  éstos son [CEvent](../../mfc/reference/cevent-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md), y [CSemaphore](../../mfc/reference/csemaphore-class.md).  
  
 Para obtener información sobre cómo utilizar los objetos de sincronización, vea el artículo [Multithreading: Cómo utilizar las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CSyncObject`  
  
## Requisitos  
 **encabezado:** afxmt.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)