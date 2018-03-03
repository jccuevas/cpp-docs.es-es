---
title: "TN025: Documentos, vistas y marcos creación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.creation
dev_langs:
- C++
helpviewer_keywords:
- documents [MFC], view and frame creation
- TN025
ms.assetid: 09254d72-6e1d-43db-80e9-693887dbeda2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 89ca395b19a36c42163b854c8997cce424352ead
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="tn025-document-view-and-frame-creation"></a>TN025: Creación de documentos, vistas y marcos
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe los problemas de creación y la propiedad para WinApps, DocTemplates, documentos, vistas y marcos.  
  
## <a name="winapp"></a>WinApp  
 Hay un `CWinApp` objeto en el sistema.  
  
 Estáticamente se crea y se inicializa por implementación interna del marco de trabajo de `WinMain`. Debe derivar de `CWinApp` que hacer nada útil (excepción: archivos DLL de extensión MFC no deben tener un `CWinApp` instancia, se realiza la inicialización `DllMain` en su lugar).  
  
 La `CWinApp` objeto posee una lista de plantillas de documento (una `CPtrList`). Hay uno o más plantillas de documento por aplicación. DocTemplates normalmente se cargan desde el archivo de recursos (es decir, una matriz de cadenas) en `CWinApp::InitInstance`.  
  
```  
pTemplate = new CDocTemplate(IDR_MYDOCUMENT, ...);

AddDocTemplate(pTemplate);
```  
  
 La `CWinApp` objeto posee todas las ventanas de marco en la aplicación. La ventana de marco principal de la aplicación debe almacenarse en **CWinApp::m_pMainWnd**; normalmente establece `m_pMainWnd` en el `InitInstance` implementación si no se permiten AppWizard lo haga por usted. Para la interfaz de único documento (SDI), esta es una `CFrameWnd` que actúa como la ventana de marco de aplicación principal, así como la ventana de marco de documento único. Para la interfaz de múltiples documentos (MDI) es un marco de MDI (clase `CMDIFrameWnd`) que actúa como la ventana de marco de aplicación principal que contiene todos los secundarios `CFrameWnd`s. Cada ventana secundaria es de clase `CMDIChildWnd` (derivado de `CFrameWnd`) y actúa como uno de potencialmente muchas ventanas de marco de documento.  
  
## <a name="doctemplates"></a>DocTemplates  
 El `CDocTemplate` es el creador y el Administrador de documentos. Posee los documentos que crea. Si la aplicación utiliza el enfoque basado en recursos que se describe a continuación, no será necesario derivar de `CDocTemplate`.  
  
 Para una aplicación SDI, la clase `CSingleDocTemplate` realiza un seguimiento de un documento abierto. Para una aplicación MDI, la clase `CMultiDocTemplate` mantiene una lista (una `CPtrList`) de todos los documentos actualmente abiertos creados a partir de dicha plantilla. `CDocTemplate::AddDocument`y `CDocTemplate::RemoveDocument` proporcionar funciones de miembro virtual para agregar o quitar un documento de la plantilla. `CDocTemplate`es un elemento friend de **CDocument** por lo que podemos establecer protegido **CDocument::m_pDocTemplate** puntero trasero para que señalen a la plantilla de documento que se creó el documento.  
  
 `CWinApp`Controla el valor predeterminado `OnFileOpen` implementación, que a su vez consultará todas las plantillas de doc. La implementación incluye busca documentos ya está abiertos y decidir qué formato para abrir documentos nuevos en.  
  
 `CDocTemplate`administra el enlace de la interfaz de usuario para los documentos y marcos.  
  
 `CDocTemplate`mantiene un recuento del número de documentos sin nombre.  
  
## <a name="cdocument"></a>CDocument  
 A **CDocument** pertenece a un `CDocTemplate`.  
  
 Documentos tienen una lista de abiertas actualmente vistas (derivado de `CView`) que está viendo el documento (una `CPtrList`).  
  
 Documentos no crear/destruir las vistas, pero están conectados entre sí después de que se creen. Cuando se cierra un documento (es decir, mediante archivo/cerrar), se cerrarán todas las vistas asociadas. Cuando se cierra la última vista en un documento (es decir, o cerrar la ventana) se cerrará el documento.  
  
 El `CDocument::AddView`, `RemoveView` interfaz se utiliza para mantener la lista de vista. **CDocument** es un elemento friend de `CView` por lo que podemos establecer la **CView::m_pDocument** puntero trasero.  
  
## <a name="cframewnd"></a>CFrameWnd  
 A `CFrameWnd` (también conocido como un marco) desempeña un papel mismo como en MFC 1.0, pero ahora el `CFrameWnd` clase está diseñada para usarse en muchos casos, sin tener que derivar una clase nueva. Las clases derivadas `CMDIFrameWnd` y `CMDIChildWnd` también se han mejorado para muchos comandos estándares ya están implementados.  
  
 El `CFrameWnd` es responsable de la creación de ventanas en el área de cliente del marco. Normalmente hay una ventana principal rellena el área de cliente del marco.  
  
 Para una ventana de marco MDI, el área de cliente se rellena con el control MDICLIENT que a su vez es el elemento primario de todas las ventanas de marco MDI secundario. Para una ventana de marco SDI o una ventana marco secundaria MDI, normalmente se rellena el área de cliente con un `CView`-deriva el objeto de ventana. En el caso de `CSplitterWnd`, el área de cliente de la vista se rellena con el `CSplitterWnd` objeto de ventana y el `CView`-objetos de ventana derivadas (uno por cada panel de división) se crean como ventanas secundarias de la `CSplitterWnd`.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

