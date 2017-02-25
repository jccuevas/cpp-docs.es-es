---
title: "CNotSupportedException Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CNotSupportedException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CNotSupportedException class"
  - "excepciones, not supported"
  - "unsupported features"
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CNotSupportedException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una excepción que es el resultado de una solicitud de una característica no compatible.  
  
## Sintaxis  
  
```  
class CNotSupportedException : public CSimpleException  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CNotSupportedException::CNotSupportedException](../Topic/CNotSupportedException::CNotSupportedException.md)|Crea un objeto `CNotSupportedException`.|  
  
## Comentarios  
 No hay ninguna otra calificación necesaria o posible.  
  
 Para obtener más información sobre cómo utilizar `CNotSupportedException`, vea el artículo [control de excepciones \(MFC\)](../../mfc/exception-handling-in-mfc.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CNotSupportedException`  
  
## Requisitos  
 **encabezado:** afx.h  
  
## Vea también  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)