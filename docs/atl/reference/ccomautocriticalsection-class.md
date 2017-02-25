---
title: "CComAutoCriticalSection Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComAutoCriticalSection"
  - "ATL::CComAutoCriticalSection"
  - "CComAutoCriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComAutoCriticalSection class"
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComAutoCriticalSection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CComAutoCriticalSection` proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.  
  
## Sintaxis  
  
```  
  
class CComAutoCriticalSection : public CComCriticalSection  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComAutoCriticalSection::CComAutoCriticalSection](../Topic/CComAutoCriticalSection::CComAutoCriticalSection.md)|el constructor.|  
|[CComAutoCriticalSection::~CComAutoCriticalSection](../Topic/CComAutoCriticalSection::~CComAutoCriticalSection.md)|El destructor.|  
  
## Comentarios  
 `CComAutoCriticalSection` es similar ordenar [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md), a menos que inicializa `CComAutoCriticalSection` automáticamente el objeto de sección crítica en el constructor.  
  
 Normalmente, se utiliza `CComAutoCriticalSection` con el nombre [AutoCriticalSection](../Topic/CComMultiThreadModel::AutoCriticalSection.md)de `typedef` .  Referencias de este nombre `CComAutoCriticalSection` cuando se utiliza [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) .  
  
 Los métodos de `Init` y de `Term` de [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) no están disponibles al utilizar esta clase.  
  
## Jerarquía de herencia  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComAutoCriticalSection`  
  
## Requisitos  
 **Header:** atlcore.h  
  
## Vea también  
 [CComFakeCriticalSection Class](../../atl/reference/ccomfakecriticalsection-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComCriticalSection Class](../../atl/reference/ccomcriticalsection-class.md)