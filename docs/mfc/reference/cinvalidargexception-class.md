---
title: "CInvalidArgException Class | Microsoft Docs"
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
  - "CInvalidArgException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInvalidArgException class"
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CInvalidArgException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase representa una condición de excepción de argumento no válido.  
  
## Sintaxis  
  
```  
  
class CInvalidArgException : public CSimpleException  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInvalidArgException::CInvalidArgException](../Topic/CInvalidArgException::CInvalidArgException.md)|el constructor.|  
  
## Comentarios  
 Un objeto de `CInvalidArgException` representa una condición de excepción de argumento no válido.  
  
 Para obtener más información sobre el control de excepciones, vea el tema y [control de excepciones \(MFC\)](../../mfc/exception-handling-in-mfc.md)de [clase de CException](../../mfc/reference/cexception-class.md) .  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CInvalidArgException`  
  
## Requisitos  
 **encabezado:** afx.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CSimpleException Class](../../mfc/reference/csimpleexception-class.md)