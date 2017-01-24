---
title: "CMultiDocTemplate Class | Microsoft Docs"
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
  - "CMultiDocTemplate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMultiDocTemplate class"
  - "MDI, plantilla"
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
caps.latest.revision: 21
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMultiDocTemplate Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Define una plantilla de documento que implementa la interfaz de múltiples \(MDI\) documentos.  
  
## Sintaxis  
  
```  
  
class CMultiDocTemplate : public CDocTemplate  
  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMultiDocTemplate::CMultiDocTemplate](../Topic/CMultiDocTemplate::CMultiDocTemplate.md)|Crea un objeto `CMultiDocTemplate`.|  
  
## Comentarios  
 Una aplicación MDI utiliza la ventana de marco principal como un área de trabajo donde el usuario pueda abrir cero o más ventana de marco de documento, que presenta un documento.  Para obtener una descripción más detallada de MDI, vea *las instrucciones de la interfaz de Windows para el diseño de software*.  
  
 Una plantilla de documento define las relaciones entre tres tipos de clases:  
  
-   Una clase de documento, que se deriva de [CDocument](../../mfc/reference/cdocument-class.md).  
  
-   Una clase de vista, que muestra los datos de la clase document enumerados anteriormente.  Puede derivar esta clase de [CView](../../mfc/reference/cview-class.md), de `CScrollView`, de `CFormView`, o de `CEditView`.  \(También puede usar `CEditView` directamente.\)  
  
-   Una clase de ventana de marco, que contiene la vista.  Para una plantilla de documento MDI, puede derivar esta clase de `CMDIChildWnd`, o, si no necesita personalizar el comportamiento de las ventanas de marco de documento, puede utilizar [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) directamente sin derivar de su propia clase.  
  
 Una aplicación MDI puede admitir más de un tipo de documento, y documentos de diferentes tipos pueden ser abiertos al mismo tiempo.  La aplicación tiene una plantilla de documento para cada tipo de documento que admite.  Por ejemplo, si su aplicación MDI admite hojas de cálculo y documentos de texto, la aplicación tiene dos objetos de `CMultiDocTemplate` .  
  
 La aplicación utiliza la plantilla de documento cuando el usuario crea un nuevo documento.  Si la aplicación admite más de un tipo de documento, el marco obtiene los nombres de los tipos de documento admitidos de plantillas de documento y las muestra en una lista del cuadro de diálogo del Archivo Nuevo.  Una vez que el usuario ha seleccionado un tipo de documento, la aplicación crea un objeto de clase de documento, un objeto de la ventana de marco, y un objeto de vista y los adjunta entre sí.  
  
 No tiene que llamar a las funciones miembro de `CMultiDocTemplate` excepto el constructor.  El marco controla los objetos de `CMultiDocTemplate` internamente.  
  
 Para obtener más información sobre `CMultiDocTemplate`, vea [Plantillas de documento y el proceso de Creación de documentos y vistas](../../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)  
  
 `CMultiDocTemplate`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [CSingleDocTemplate Class](../../mfc/reference/csingledoctemplate-class.md)   
 [CWinApp Class](../../mfc/reference/cwinapp-class.md)