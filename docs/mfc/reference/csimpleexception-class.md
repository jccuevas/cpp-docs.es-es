---
title: "CSimpleException Class | Microsoft Docs"
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
  - "CSimpleException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleException class"
ms.assetid: be0eb8ef-e5b9-47d6-b0fb-efaff2d1e666
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSimpleException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase es una clase base para las excepciones recurso\-críticas MFC.  
  
## Sintaxis  
  
```  
  
class AFX_NOVTABLE CSimpleException : public CException  
  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleException::CSimpleException](../Topic/CSimpleException::CSimpleException.md)|el constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleException::GetErrorMessage](../Topic/CSimpleException::GetErrorMessage.md)|Proporciona el texto sobre un error que se ha producido.|  
  
## Comentarios  
 `CSimpleException` es la clase base para las excepciones recurso\-críticas de MFC y controla la propiedad y la inicialización de un mensaje de error.  Las siguientes clases utilizan `CSimpleException` como clase base:  
  
|||  
|-|-|  
|[clase de CMemoryException](../../mfc/reference/cmemoryexception-class.md)|excepción de memoria insuficiente|  
|[clase de CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Pedidos una operación no compatibles|  
|[clase de CResourceException](../../mfc/reference/cresourceexception-class.md)|Recursos de Windows no encontrado no pueden crearse|  
|[clase de CUserException](../../mfc/reference/cuserexception-class.md)|La excepción que indica un recurso no se ha podido encontrar|  
|[clase de CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Excepción que indica un argumento no válido|  
  
 Dado que `CSimpleException` es una clase base abstracta, no puede declarar un objeto de `CSimpleException` directamente.  En su lugar, debe declarar objetos derivados como los de la tabla anterior.  Si se declara dispone de la clase derivada, utilice las clases anteriores como modelo.  
  
 Para obtener más información, vea el tema y [control de excepciones \(MFC\)](../../mfc/exception-handling-in-mfc.md)de [clase de CException](../../mfc/reference/cexception-class.md) .  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CSimpleException`  
  
## Requisitos  
 **encabezado:** afx.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CException Class](../../mfc/reference/cexception-class.md)   
 [Control de excepciones](../../mfc/exception-handling-in-mfc.md)