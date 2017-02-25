---
title: "CArchiveException Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CArchiveException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archive exceptions [C++]"
  - "CArchiveException class"
  - "exceptions [C++], archive"
  - "exceptions [C++], serialización"
  - "serialización [C++], excepciones"
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CArchiveException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una condición de excepción de serialización  
  
## Sintaxis  
  
```  
class CArchiveException : public CException  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CArchiveException::CArchiveException](../Topic/CArchiveException::CArchiveException.md)|Crea un objeto `CArchiveException`.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CArchiveException::m\_cause](../Topic/CArchiveException::m_cause.md)|indica la causa de la excepción.|  
|[CArchiveException::m\_strFileName](../Topic/CArchiveException::m_strFileName.md)|Especifica el nombre del archivo de esta condición de excepción.|  
  
## Comentarios  
 La clase de `CArchiveException` incluye un miembro de datos público que indica la causa de la excepción.  
  
 se crean los objetos de`CArchiveException` y funciones interiores producidas miembro de [CArchive](../../mfc/reference/carchive-class.md) .  Puede tener acceso a estos objetos dentro del ámbito de una expresión de **CATCH** .  El código de la causa es independiente del sistema operativo.  Para obtener más información sobre el procesamiento de excepciones, vea [control de excepciones \(MFC\)](../../mfc/exception-handling-in-mfc.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CArchiveException`  
  
## Requisitos  
 **encabezado:** afx.h  
  
## Vea también  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CArchive Class](../../mfc/reference/carchive-class.md)   
 [AfxThrowArchiveException](../Topic/AfxThrowArchiveException.md)   
 [Procesamiento de excepciones](../../mfc/reference/exception-processing.md)