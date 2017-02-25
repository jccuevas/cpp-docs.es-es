---
title: "CMemoryException Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMemoryException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de excepciones de C++, memoria"
  - "CMemoryException class"
  - "excepciones, memory type"
  - "memory exceptions"
  - "memoria, control de excepciones"
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CMemoryException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una condición de excepción de memoria insuficiente.  
  
## Sintaxis  
  
```  
class CMemoryException : public CSimpleException  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMemoryException::CMemoryException](../Topic/CMemoryException::CMemoryException.md)|Crea un objeto `CMemoryException`.|  
  
## Comentarios  
 No hay ninguna otra calificación necesaria o posible.  Las excepciones de memoria se inician automáticamente **nuevo**.  Si escribe posee las funciones de memoria, mediante `malloc`, por ejemplo, entonces es responsable de producir excepciones de memoria.  
  
 Para obtener más información sobre `CMemoryException`, vea el artículo [control de excepciones \(MFC\)](../../mfc/exception-handling-in-mfc.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CMemoryException`  
  
## Requisitos  
 **encabezado:** afx.h  
  
## Vea también  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)