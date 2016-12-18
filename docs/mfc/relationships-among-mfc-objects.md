---
title: "Relaciones entre objetos MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "relaciones de objeto MFC"
  - "MFC, relaciones entre objetos clave"
  - "objetos [C++], relaciones"
  - "relaciones, objetos MFC"
ms.assetid: 6e8f3b51-e80f-4d88-94c8-4c1e4ee163ad
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Relaciones entre objetos MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para ayudar coloque el proceso de creación de documento y vista en perspectiva, vea un programa en ejecución: un documento, la ventana de marco utilizada para contener la vista, y la vista asociada al documento.  
  
-   Un documento mantiene una lista de las vistas de ese documento y un puntero a la plantilla de documento que creó el documento.  
  
-   Una vista mantiene un puntero al documento y es un elemento secundario de la ventana de marco principal.  
  
-   Una ventana de marco de documento mantiene un puntero a la vista activa actual.  
  
-   Una plantilla de documento mantiene una lista de los documentos abiertos.  
  
-   La aplicación mantiene una lista de las plantillas de documento.  
  
-   Windows realiza un seguimiento de todas las ventanas abiertas de modo que puede enviarles mensajes.  
  
 Estas relaciones se establecen durante la creación de documentos y vistas.  La tabla siguiente se muestra cómo los objetos en un programa en ejecución pueden tener acceso a otros objetos.  Cualquier objeto puede obtener un puntero al objeto application llamando a la función global [AfxGetApp](../Topic/AfxGetApp.md).  
  
### Acceso a objetos de Otros en la aplicación de El  
  
|De objeto|Cómo tener acceso a otros objetos|  
|---------------|---------------------------------------|  
|Documento|Utilice [GetFirstViewPosition](../Topic/CDocument::GetFirstViewPosition.md) y [GetNextView](../Topic/CDocument::GetNextView.md) para tener acceso a la lista de la vista del documento.<br /><br /> Llamada [GetDocTemplate](../Topic/CDocument::GetDocTemplate.md) para obtener la plantilla de documento.|  
|View|Llamada [GetDocument](../Topic/CView::GetDocument.md) para obtener el documento.<br /><br /> Llamada [GetParentFrame](../Topic/CWnd::GetParentFrame.md) para obtener la ventana de marco.|  
|Ventana de marco de documento|Llamada [GetActiveView](../Topic/CFrameWnd::GetActiveView.md) para obtener la vista actual.<br /><br /> Llame a [GetActiveDocument](../Topic/CFrameWnd::GetActiveDocument.md) para obtener el documento asociado a la vista actual.|  
|Ventana de marco MDI|Llame a [MDIGetActive](../Topic/CMDIFrameWnd::MDIGetActive.md) para obtener actualmente [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)activo.|  
  
 Normalmente, una ventana de marco tiene una vista, pero a veces, como en ventanas divisoras, la misma ventana de marco contiene varias vistas.  La ventana de marco mantiene un puntero actualmente a la vista activa; se actualiza el puntero cualquier momento se produce otra vista.  
  
> [!NOTE]
>  Un puntero a la ventana de marco principal se almacena en la variable miembro de [m\_pMainWnd](../Topic/CWinThread::m_pMainWnd.md) del objeto application.  Una llamada a `OnFileNew` en el reemplazo de la función miembro de `InitInstance` de `CWinApp` establece `m_pMainWnd` automáticamente.  Si no llama `OnFileNew`, debe establecer el valor de variable en `InitInstance` personalmente. Las aplicaciones componentes COM \(SDI \(servidor\) pueden no establecer la variable si \/Embedding está en la línea de comandos\). Observe que `m_pMainWnd` ahora es miembro de la clase `CWinThread` en lugar de `CWinApp`.  
  
## Vea también  
 [Plantillas de documento y el proceso de creación de documentos y vistas](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Clear plantillas de documentos](../mfc/document-template-creation.md)   
 [Crear documentos y vistas](../mfc/document-view-creation.md)   
 [Crear nuevos documentos, ventanas y vistas](../mfc/creating-new-documents-windows-and-views.md)