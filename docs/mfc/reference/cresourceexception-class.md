---
title: "CResourceException Class | Microsoft Docs"
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
  - "CResourceException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CResourceException class"
  - "excepciones, recurso"
  - "resource allocation exception"
  - "resource exceptions"
  - "recursos [C++], asignar"
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CResourceException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se genera cuando Windows no puede encontrar o asignar un recurso solicitado.  
  
## Sintaxis  
  
```  
class CResourceException : public CSimpleException  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CResourceException::CResourceException](../Topic/CResourceException::CResourceException.md)|Crea un objeto `CResourceException`.|  
  
## Comentarios  
 No hay ninguna otra calificación necesaria o posible.  
  
 Para obtener más información sobre cómo utilizar `CResourceException`, vea el artículo [control de excepciones \(MFC\)](../../mfc/exception-handling-in-mfc.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CResourceException`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)