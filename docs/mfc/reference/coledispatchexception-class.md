---
title: "COleDispatchException Class | Microsoft Docs"
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
  - "COleDispatchException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "automatización, excepciones"
  - "COleDispatchException class"
  - "excepciones, OLE"
  - "OLE exceptions, to IDispatch interface"
ms.assetid: 0e95c8be-e21a-490c-99ec-181c6a9a26d0
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleDispatchException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Controla las excepciones específicas de la interfaz OLE de `IDispatch` , que es una parte fundamental de automatización OLE.  
  
## Sintaxis  
  
```  
class COleDispatchException : public CException  
```  
  
## Miembros  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDispatchException::m\_dwHelpContext](../Topic/COleDispatchException::m_dwHelpContext.md)|Contexto de Ayuda para el error.|  
|[COleDispatchException::m\_strDescription](../Topic/COleDispatchException::m_strDescription.md)|Descripción del error verbal.|  
|[COleDispatchException::m\_strHelpFile](../Topic/COleDispatchException::m_strHelpFile.md)|Archivo de Ayuda a utilizar con `m_dwHelpContext`.|  
|[COleDispatchException::m\_strSource](../Topic/COleDispatchException::m_strSource.md)|Aplicación que generó la excepción.|  
|[COleDispatchException::m\_wCode](../Topic/COleDispatchException::m_wCode.md)|`IDispatch`\- código de error específico.|  
  
## Comentarios  
 Como las demás clases de excepción derivadas de la clase base de `CException` , `COleDispatchException` se puede utilizar con **THROW**, `THROW_LAST`, **TRY**, **CATCH**, `AND_CATCH`, y las macros de `END_CATCH` .  
  
 Debe llamar a normalmente [AfxThrowOleDispatchException](../Topic/AfxThrowOleDispatchException.md) para crear y para iniciar un objeto de `COleDispatchException` .  
  
 Para obtener más información sobre excepciones, vea los artículos [control de excepciones \(MFC\)](../../mfc/exception-handling-in-mfc.md) y [excepciones: OLE Exceptions](../../mfc/exceptions-ole-exceptions.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `COleDispatchException`  
  
## Requisitos  
 **encabezado:** afxdisp.h  
  
## Vea también  
 [ejemplo CALCDRIV de MFC](../../top/visual-cpp-samples.md)   
 [CException Class](../../mfc/reference/cexception-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDispatchDriver Class](../../mfc/reference/coledispatchdriver-class.md)   
 [COleException Class](../../mfc/reference/coleexception-class.md)