---
title: 'TN025: Documento, vista y creación de marco'
ms.date: 11/04/2016
f1_keywords:
- vc.creation
helpviewer_keywords:
- documents [MFC], view and frame creation
- TN025
ms.assetid: 09254d72-6e1d-43db-80e9-693887dbeda2
ms.openlocfilehash: 4958e7c4ca2c3cf9eed6420d72d0399fa112098d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306001"
---
# <a name="tn025-document-view-and-frame-creation"></a>TN025: Documento, vista y creación de marco

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota describe los problemas de creación y la propiedad para WinApps, DocTemplates, documentos, vistas y marcos.

## <a name="winapp"></a>WinApp

Hay un `CWinApp` objeto en el sistema.

Estáticamente se crea y se inicializa mediante la implementación interna del marco de trabajo de `WinMain`. Debe derivar de `CWinApp` que hacer nada útil (excepción: DLL de extensión MFC no debe tener un `CWinApp` instancia, se realiza en `DllMain` en su lugar).

El `CWinApp` objeto posee una lista de plantillas de documento (un `CPtrList`). Hay uno o más plantilla de documento por aplicación. DocTemplates normalmente se cargan desde el archivo de recursos (es decir, una matriz de cadenas) en `CWinApp::InitInstance`.

```
pTemplate = new CDocTemplate(IDR_MYDOCUMENT, ...);

AddDocTemplate(pTemplate);
```

La `CWinApp` objeto posee todas las ventanas de marco en la aplicación. La ventana de marco principal de la aplicación debe almacenarse en `CWinApp::m_pMainWnd`; normalmente establece *m_pMainWnd* en el `InitInstance` implementación si no se permiten AppWizard lo hará por usted. Para la interfaz de único documento (SDI), esta es una `CFrameWnd` que actúa como la ventana de marco principal de la aplicación, así como la ventana de marco de documento único. Para la interfaz de múltiples documentos (MDI) es un marco de MDI (clase `CMDIFrameWnd`) que actúa como la ventana de marco principal de la aplicación que contiene todos los secundarios `CFrameWnd`s. Cada ventana secundaria es de clase `CMDIChildWnd` (derivado de `CFrameWnd`) y actúa como una de muchas ventanas de marco de documento.

## <a name="doctemplates"></a>DocTemplates

El `CDocTemplate` es el creador y Administrador de documentos. Posee los documentos que crea. Si la aplicación utiliza el enfoque basado en recursos se describen a continuación, no necesitará derivar de `CDocTemplate`.

Para una aplicación SDI, la clase `CSingleDocTemplate` realiza un seguimiento de un documento abierto. Para una aplicación MDI, la clase `CMultiDocTemplate` mantiene una lista (un `CPtrList`) de todos los documentos abiertos actualmente creados a partir de esa plantilla. `CDocTemplate::AddDocument` y `CDocTemplate::RemoveDocument` proporcionan funciones de miembro virtual para agregar o quitar un documento de la plantilla. `CDocTemplate` es de confianza `CDocument` por lo que podemos establecer protegido `CDocument::m_pDocTemplate` puntero para que señalen a la plantilla de documento que se creó el documento.

`CWinApp` Controla el valor predeterminado `OnFileOpen` implementación, que a su vez consultará todas las plantillas de doc. La implementación incluye buscando documentos ya está abiertos y decidir qué formato se van a abrir documentos nuevos en.

`CDocTemplate` administra el enlace de la interfaz de usuario para los documentos y marcos.

`CDocTemplate` mantiene un recuento del número de documentos sin nombre.

## <a name="cdocument"></a>CDocument

Un `CDocument` pertenece a un `CDocTemplate`.

Los documentos tienen una lista de actualmente abrir vistas (derivado de `CView`) que está viendo el documento (un `CPtrList`).

Documentos no crean/destruyen las vistas, pero que están conectados entre sí después de que se creen. Cuando se cierra un documento (es decir, al archivo/cerrar), se cerrarán todas las vistas adjuntadas. Cuando se cierra la última vista en un documento (es decir, o cerrar la ventana), se cerrará el documento.

El `CDocument::AddView`, `RemoveView` interfaz se usa para mantener la vista de lista. `CDocument` es de confianza `CView` por lo que podemos establecer el `CView::m_pDocument` puntero trasero.

## <a name="cframewnd"></a>CFrameWnd

Un `CFrameWnd` (también conocido como un marco) reproduce el mismo rol como en MFC 1.0, pero ahora el `CFrameWnd` clase está diseñada para usarse en muchos casos sin que derivar una clase nueva. Las clases derivadas `CMDIFrameWnd` y `CMDIChildWnd` también se han mejorado para muchos comandos estándares ya están implementados.

El `CFrameWnd` es responsable de la creación de ventanas en el área cliente del marco. Normalmente hay una ventana principal rellena el área cliente del marco.

Para una ventana de marco de MDI, el área de cliente se rellena con el control MDICLIENT que a su vez es el elemento primario de todas las ventanas de marco MDI secundario. Para una ventana de marco de SDI o una ventana de marco MDI secundario, normalmente se rellena el área de cliente con un `CView`-derivados el objeto de ventana. En el caso de `CSplitterWnd`, el área de cliente de la vista se rellena con el `CSplitterWnd` objeto window y el `CView`-objetos de ventana derivadas (uno por cada panel de división) se crean como ventanas secundarias de la `CSplitterWnd`.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
