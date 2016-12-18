---
title: "COleException Class | Microsoft Docs"
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
  - "COleException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleException class"
  - "excepciones, OLE"
ms.assetid: 2571e9fe-26cc-42f0-9ad9-8ad5b4311ec1
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una condición de excepción relacionada con una operación\).  
  
## Sintaxis  
  
```  
class COleException : public CException  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleException::Process](../Topic/COleException::Process.md)|Traduce una excepción detectada a un código de retorno OLE.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleException::m\_sc](../Topic/COleException::m_sc.md)|Contiene el código de estado que indica la razón de la excepción.|  
  
## Comentarios  
 La clase de `COleException` incluye un miembro de datos público que contiene el código de estado que indica la razón de la excepción.  
  
 No debe crear normalmente un objeto de `COleException` directamente; en su lugar, debe llamar a [AfxThrowOleException](../Topic/AfxThrowOleException.md).  
  
 Para obtener más información sobre excepciones, vea los artículos [control de excepciones \(MFC\)](../../mfc/exception-handling-in-mfc.md) y [excepciones: OLE Exceptions](../../mfc/exceptions-ole-exceptions.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `COleException`  
  
## Requisitos  
 **encabezado:** afxdisp.h  
  
## Vea también  
 [ejemplo CALCDRIV de MFC](../../top/visual-cpp-samples.md)   
 [CException Class](../../mfc/reference/cexception-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)