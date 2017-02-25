---
title: "CHandle Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CHandle"
  - "ATL::CHandle"
  - "CHandle"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHandle class"
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CHandle Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para crear y utilizar un objeto ID.  
  
## Sintaxis  
  
```  
  
class CHandle  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHandle::CHandle](../Topic/CHandle::CHandle.md)|el constructor.|  
|[CHandle::~CHandle](../Topic/CHandle::~CHandle.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHandle::Attach](../Topic/CHandle::Attach.md)|Llame a este método para asociar el objeto de `CHandle` un identificador existente.|  
|[CHandle::Close](../Topic/CHandle::Close.md)|Llame a este método para cerrar un objeto de `CHandle` .|  
|[CHandle::Detach](../Topic/CHandle::Detach.md)|Llame a este método para desasociar el identificador de un objeto de `CHandle` .|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHandle::operator HANDLE](../Topic/CHandle::operator%20HANDLE.md)|Devuelve el valor de identificador almacenado.|  
|[CHandle::operator \=](../Topic/CHandle::operator%20=.md)|Operador de asignación.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHandle::m\_h](../Topic/CHandle::m_h.md)|la variable miembro que almacena el identificador.|  
  
## Comentarios  
 Un objeto de `CHandle` puede utilizar siempre que se requiera un identificador: la diferencia principal es que el objeto de `CHandle` automáticamente se eliminará.  
  
> [!NOTE]
>  Algunas funciones API utilizarán NULL como identificador vacío o no válido, mientras que otras utilizan INVALID\_HANDLE\_VALUE.  `CHandle` sólo utiliza NULL y tratará INVALID\_HANDLE\_VALUE como identificador real.  Si se llama a la API que pueden devolver INVALID\_HANDLE\_VALUE, debe comprobar este valor antes de llamar [CHandle:: Asociar](../Topic/CHandle::Attach.md) o de pasarlo al constructor de `CHandle` y, en su lugar pasa NULL.  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)