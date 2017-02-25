---
title: "CInternetException Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CInternetException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInternetException class"
  - "control de excepciones, Internet operations"
  - "excepciones, Internet"
ms.assetid: 44fb3cbe-523e-4754-8843-a77909990b14
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CInternetException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una condición de excepción relacionada con una operación de internet.  
  
## Sintaxis  
  
```  
class CInternetException : public CException  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInternetException::CInternetException](../Topic/CInternetException::CInternetException.md)|Crea un objeto `CInternetException`.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInternetException::m\_dwContext](../Topic/CInternetException::m_dwContext.md)|El valor de contexto asociado a la operación que produjo la excepción.|  
|[CInternetException::m\_dwError](../Topic/CInternetException::m_dwError.md)|El error que provocó la excepción.|  
  
## Comentarios  
 La clase de `CInternetException` incluye dos miembros de datos públicos: uno contiene el código de error asociado a la excepción, y el otro contiene el identificador de contexto de la aplicación de internet asociada al error.  
  
 Para obtener más información sobre los identificadores de contexto para las aplicaciones de internet, vea el artículo [Internet que programa con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CInternetException`  
  
## Requisitos  
 **encabezado:** afxinet.h  
  
## Vea también  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CException Class](../../mfc/reference/cexception-class.md)