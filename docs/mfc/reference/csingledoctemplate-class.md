---
title: "CSingleDocTemplate Class | Microsoft Docs"
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
  - "CSingleDocTemplate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSingleDocTemplate class"
  - "plantillas de documento, single"
  - "interfaz de único documento (SDI), aplicaciones"
  - "plantillas, SDI"
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSingleDocTemplate Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

define una plantilla de documento que implemente la interfaz de un único documento \(SDI\).  
  
## Sintaxis  
  
```  
class CSingleDocTemplate : public CDocTemplate  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSingleDocTemplate::CSingleDocTemplate](../Topic/CSingleDocTemplate::CSingleDocTemplate.md)|Crea un objeto `CSingleDocTemplate`.|  
  
## Comentarios  
 Una aplicación SDI utiliza la ventana de marco principal para mostrar un documento; sólo un documento puede ser abiertos al mismo tiempo.  
  
 Una plantilla de documento define la relación entre tres tipos de clases:  
  
-   Una clase de documento, que se deriva de **CDocument**.  
  
-   Una clase de vista, que muestra los datos de la clase document enumerados anteriormente.  Puede derivar esta clase de `CView`, de `CScrollView`, de `CFormView`, o de `CEditView`.  \(También puede usar `CEditView` directamente.\)  
  
-   Una clase de ventana de marco, que contiene la vista.  Para una plantilla de documento SDI, puede derivar esta clase de `CFrameWnd`; si no necesita personalizar el comportamiento de la ventana de marco principal, puede utilizar `CFrameWnd` directamente sin derivar de su propia clase.  
  
 Una aplicación SDI admite normalmente un tipo de documento, por lo que solo tiene un objeto de `CSingleDocTemplate` .  Sólo un documento puede ser abiertos al mismo tiempo.  
  
 No tiene que llamar a las funciones miembro de `CSingleDocTemplate` excepto el constructor.  El marco controla los objetos de `CSingleDocTemplate` internamente.  
  
 Para obtener más información sobre cómo utilizar `CSingleDocTemplate`, vea [Plantillas de documento y el proceso de Creación de documentos y vistas](../../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)  
  
 `CSingleDocTemplate`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo DOCKTOOL de MFC](../../top/visual-cpp-samples.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [CDocument Class](../../mfc/reference/cdocument-class.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [CMultiDocTemplate Class](../../mfc/reference/cmultidoctemplate-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CWinApp Class](../../mfc/reference/cwinapp-class.md)