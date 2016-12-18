---
title: "TN025: Creaci&#243;n de documentos, vistas y marcos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.creation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "documentos, creación de vistas y marcos"
  - "TN025"
ms.assetid: 09254d72-6e1d-43db-80e9-693887dbeda2
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN025: Creaci&#243;n de documentos, vistas y marcos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe los problemas de la creación y la propiedad de WinApps, DocTemplates, documentos, frames y vistas.  
  
## WinApp  
 Hay un objeto de `CWinApp` en el sistema.  
  
 Es construido e inicializar estáticamente mediante la implementación interna de `WinMain`.  Debe derivar de `CWinApp` para hacer nada útil \(excepción: los archivos DLL de extensión no deben tener una instancia de `CWinApp` — inicialización se hace en `DllMain` en su lugar\).  
  
 El objeto de `CWinApp` posee una lista de plantillas de documento \( `CPtrList`\).  Hay una o más plantillas de documentos por la aplicación.  DocTemplates se carga normalmente del archivo de recursos \(es decir, una matriz de cadenas\) en `CWinApp::InitInstance`.  
  
```  
pTemplate = new CDocTemplate(IDR_MYDOCUMENT, ...);  
AddDocTemplate(pTemplate);  
```  
  
 El objeto de `CWinApp` posee todas las ventanas de marco en la aplicación.  La ventana de marco principal para la aplicación se debe almacenar en **CWinApp::m\_pMainWnd**; se `m_pMainWnd` establecido en la implementación de `InitInstance` si no está desusado AppWizard hace normalmente para usted.  Para la interfaz de un único documento \(SDI\) el es un `CFrameWnd` que actúa como la ventana de marco principal de la aplicación así como única ventana de marco de documento.  Para la interfaz de múltiples documentos \(MDI\) es MDI\- cuadro \(clase `CMDIFrameWnd`\) que actúa como la ventana de marco principal de la aplicación que contiene toda la s secundaria de `CFrameWnd`.  Cada ventana secundaria es de clase `CMDIChildWnd` \(derivado de `CFrameWnd`\) y actúa como una potencialmente muchas ventanas de marco de documento.  
  
## DocTemplates  
 `CDocTemplate` es el generador y el administrador de documentos.  Posee los documentos que crea.  Si la aplicación utiliza el enfoque basado recurso se describe más adelante, no necesitará derivar de `CDocTemplate`.  
  
 Para una aplicación SDI, la clase `CSingleDocTemplate` realiza el seguimiento de un documento abierto.  Para una aplicación MDI, la clase `CMultiDocTemplate` conserva una lista \( `CPtrList`\) de todos los actualmente documentos abiertos creados a partir de esa plantilla.  `CDocTemplate::AddDocument` y `CDocTemplate::RemoveDocument` proporcionan las funciones virtuales miembro para agregar o quitar un documento de la plantilla.  `CDocTemplate` es una función friend de **CDocument** así que podemos establecer el puntero protegido de reserva de **CDocument::m\_pDocTemplate** para señalar a doc la plantilla que creó el documento.  
  
 `CWinApp` controla la implementación predeterminada de `OnFileOpen` , que a su vez verá todas las plantillas de documento.  La implementación incluye búsqueda ya documentos abiertos y decidir en qué formato a abrir documentos nuevos.  
  
 `CDocTemplate` administra la interfaz de usuario que se enlaza para documentos y cuadros.  
  
 `CDocTemplate` mantiene un recuento del número de documentos sin nombre.  
  
## CDocument  
 **CDocument** es propiedad de `CDocTemplate`.  
  
 Los documentos tienen una lista de vistas actualmente abierto \(derivadas de `CView`\) que se consulta el documento \( `CPtrList`\).  
  
 Documentos no se crean y destruyen las vistas, pero se asocian entre sí una vez creados.  Cuando se cierra un documento \(es decir, con el archivo o el cierre\), todas las vistas asociadas se cerradas.  Cuando se cierra la vista última en un documento \(es decir, ventana\/cierre\) el documento se cierra.  
  
 `CDocument::AddView`, interfaz de `RemoveView` se utiliza para mantener la lista de vista.  **CDocument** es una función friend de `CView` así que podemos establecer el puntero de reserva de **CView::m\_pDocument** .  
  
## CFrameWnd  
 `CFrameWnd` \(también conocido como un cuadro\) reproduce el mismo rol que en MFC 1,0, pero ahora la clase de `CFrameWnd` está diseñado para utilizarse en muchos casos sin la derivación de una nueva clase.  Las clases derivadas `CMDIFrameWnd` y `CMDIChildWnd` también se mejoran en muchos comandos estándar ya se implementan.  
  
 `CFrameWnd` es responsable de crear ventanas en el área cliente del marco.  Normalmente hay una ventana principal que rellena el área cliente del marco.  
  
 Para una ventana de MDI\- cuadro, el área cliente se rellena con el control de MDICLIENT que es a su vez el elemento primario de todas las ventanas de marco de MDI\- elemento secundario.  Para una ventana de SDI\- cuadro o una ventana de marco de MDI\- elemento secundario, el área cliente se rellena normalmente con `CView`\- objeto derivado de la ventana.  En el caso de `CSplitterWnd`, el área de cliente de la vista se rellena con el objeto de la ventana de `CSplitterWnd` , y `CView`\- objetos derivados de la ventana \(uno por el panel dividido\) se crean como ventanas secundarias de `CSplitterWnd`.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)