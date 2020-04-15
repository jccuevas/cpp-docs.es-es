---
title: 'TN025: Creación de documentos, vistas y marcos'
ms.date: 11/04/2016
f1_keywords:
- vc.creation
helpviewer_keywords:
- documents [MFC], view and frame creation
- TN025
ms.assetid: 09254d72-6e1d-43db-80e9-693887dbeda2
ms.openlocfilehash: 2fdabdcb1a87d4a5661348588d49303290c966ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370367"
---
# <a name="tn025-document-view-and-frame-creation"></a>TN025: Creación de documentos, vistas y marcos

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota describe los problemas de creación y propiedad de WinApps, DocTemplates, Documentos, Marcos y Vistas.

## <a name="winapp"></a>WinApp

Hay un `CWinApp` objeto en el sistema.

Se construye e inicializa estáticamente mediante la implementación `WinMain`interna del marco de trabajo de . Debe derivar `CWinApp` de hacer algo útil (excepción: los archivos `CWinApp` DLL de extensión `DllMain` MFC no deben tener una instancia: la inicialización se realiza en su lugar).

El `CWinApp` objeto one posee una lista `CPtrList`de plantillas de documento (a ). Hay una o más plantillas de documento por aplicación. DocTemplates normalmente se cargan desde el archivo de `CWinApp::InitInstance`recursos (es decir, una matriz de cadenas) en .

```
pTemplate = new CDocTemplate(IDR_MYDOCUMENT, ...);

AddDocTemplate(pTemplate);
```

El `CWinApp` objeto one posee todas las ventanas de marco de la aplicación. La ventana de marco principal de `CWinApp::m_pMainWnd`la aplicación debe almacenarse en ; normalmente *m_pMainWnd* se establece `InitInstance` m_pMainWnd en la implementación si no ha dejado que AppWizard lo haga por usted. Para la interfaz de documento `CFrameWnd` único (SDI), esta es una que sirve como la ventana de marco de aplicación principal, así como la única ventana de marco de documento. Para la interfaz de varios documentos (MDI) se trata de un MDI-Frame (clase) `CMDIFrameWnd`que sirve como la ventana de marco de aplicación principal que contiene todos los secundarios `CFrameWnd`s. Cada ventana secundaria `CMDIChildWnd` es de `CFrameWnd`clase (derivada de ) y sirve como una de las muchas ventanas de marco de documento potencialmente.

## <a name="doctemplates"></a>DocTemplates

Es `CDocTemplate` el creador y gestor de documentos. Es el propietario de los documentos que crea. Si la aplicación usa el enfoque basado en recursos que `CDocTemplate`se describe a continuación, no tendrá que derivar de .

Para una aplicación SDI, la clase `CSingleDocTemplate` realiza un seguimiento de un documento abierto. Para una aplicación MDI, la `CMultiDocTemplate` clase `CPtrList`mantiene una lista (a ) de todos los documentos abiertos actualmente creados a partir de esa plantilla. `CDocTemplate::AddDocument`y `CDocTemplate::RemoveDocument` proporcionar las funciones miembro virtuales para agregar o quitar un documento de la plantilla. `CDocTemplate`es un `CDocument` amigo de por `CDocument::m_pDocTemplate` lo que podemos establecer el puntero de retroceso protegido para que apunte de nuevo a la plantilla de documento que creó el documento.

`CWinApp`controla `OnFileOpen` la implementación predeterminada, que a su vez consultará todas las plantillas de documento. La implementación incluye buscar documentos ya abiertos y decidir en qué formato abrir nuevos documentos.

`CDocTemplate`administra el enlace de la interfaz de usuario para documentos y marcos.

`CDocTemplate`mantiene un recuento del número de documentos sin nombre.

## <a name="cdocument"></a>CDocument

A `CDocument` es propiedad `CDocTemplate`de un archivo .

Los documentos tienen una lista de `CView`vistas abiertas actualmente `CPtrList`(derivadas de ) que están visualizando el documento (a ).

Los documentos no crean ni destruyen las vistas, pero se adjuntan entre sí después de crearlas. Cuando se cierra un documento (es decir, a través de Archivo/Cerrar), se cerrarán todas las vistas adjuntas. Cuando se cierra la última vista de un documento (es decir, Ventana/Cerrar) el documento se cerrará.

La `CDocument::AddView` `RemoveView` interfaz , se utiliza para mantener la lista de vistas. `CDocument`es un `CView` amigo de así `CView::m_pDocument` que podemos establecer el puntero de espalda.

## <a name="cframewnd"></a>CFrameWnd

A `CFrameWnd` (también conocido como marco) desempeña el mismo papel que en `CFrameWnd` MFC 1.0, pero ahora la clase está diseñada para usarse en muchos casos sin derivar una nueva clase. Las clases `CMDIFrameWnd` `CMDIChildWnd` derivadas y también se mejoran por lo que muchos comandos estándar ya están implementados.

El `CFrameWnd` es responsable de crear ventanas en el área de cliente del marco. Normalmente hay una ventana principal que llena el área de cliente del marco.

Para una ventana MDI-Frame, el área de cliente se rellena con el control MDICLIENT que es a su vez el elemento primario de todas las ventanas de marco MDI-Child. Para una ventana SDI-Frame o una ventana de marco MDI-Child, el área de cliente normalmente se rellena con un `CView`objeto de ventana derivado. En el `CSplitterWnd`caso de , el área de `CSplitterWnd` cliente de `CView`la vista se rellena con el objeto de ventana `CSplitterWnd`y los objetos de ventana derivados (uno por panel de división) se crean como ventanas secundarias del archivo .

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
