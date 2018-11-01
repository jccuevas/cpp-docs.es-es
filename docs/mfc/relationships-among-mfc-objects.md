---
title: Relaciones entre objetos MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, relationships between key objects
- objects [MFC], relationships
- relationships, MFC objects
- MFC object relationships
ms.assetid: 6e8f3b51-e80f-4d88-94c8-4c1e4ee163ad
ms.openlocfilehash: c02cf723ee7711ec1bfe00841c90bbde8c260ac1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585515"
---
# <a name="relationships-among-mfc-objects"></a>Relaciones entre objetos MFC

Para ayudar a poner el proceso de creación de documento/vista en perspectiva, considere la posibilidad de un programa en ejecución: un documento, la ventana de marco que se usa para contener la vista y la vista asociada al documento.

- Un documento conserva una lista de las vistas de ese documento y un puntero a la plantilla de documento que se creó el documento.

- Una vista mantiene un puntero a su documento y es un elemento secundario de su ventana de marco principal.

- Una ventana de marco de documento mantiene un puntero a su vista activa actual.

- Una plantilla de documento conserva una lista de los documentos abiertos.

- La aplicación mantiene una lista de las plantillas de documento.

- Windows realiza un seguimiento de todas las ventanas abiertas, por lo que puede enviar mensajes a ellos.

Estas relaciones se establecen durante la creación de documento/vista. En la tabla siguiente se muestra cómo pueden tener acceso a otros objetos de objetos en un programa en ejecución. Cualquier objeto puede obtener un puntero al objeto de aplicación mediante una llamada a la función global [AfxGetApp](../mfc/reference/application-information-and-management.md#afxgetapp).

### <a name="gaining-access-to-other-objects-in-your-application"></a>Obtener acceso a otros objetos en la aplicación

|Del objeto|Cómo obtener acceso a otros objetos|
|-----------------|---------------------------------|
|Documento|Use [GetFirstViewPosition](../mfc/reference/cdocument-class.md#getfirstviewposition) y [GetNextView](../mfc/reference/cdocument-class.md#getnextview) para tener acceso a la lista de vista del documento.<br /><br /> Llame a [GetDocTemplate](../mfc/reference/cdocument-class.md#getdoctemplate) para obtener la plantilla de documento.|
|Ver|Llame a [GetDocument](../mfc/reference/cview-class.md#getdocument) para obtener el documento.<br /><br /> Llame a [GetParentFrame](../mfc/reference/cwnd-class.md#getparentframe) para obtener la ventana de marco.|
|Ventana de marco de documento|Llame a [GetActiveView](../mfc/reference/cframewnd-class.md#getactiveview) para obtener la vista actual.<br /><br /> Llame a [GetActiveDocument](../mfc/reference/cframewnd-class.md#getactivedocument) para obtener el documento asociado a la vista actual.|
|Ventana de marco MDI|Llame a [MDIGetActive](../mfc/reference/cmdiframewnd-class.md#mdigetactive) para obtener el activo [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md).|

Normalmente, una ventana de marco tiene una vista, pero a veces, al igual que en las ventanas divisoras, la misma ventana de marco contiene varias vistas. La ventana de marco mantiene un puntero a la vista activa; el puntero se actualiza cada vez que se activa otra vista.

> [!NOTE]
>  Un puntero a la ventana de marco principal se almacena en el [m_pMainWnd](../mfc/reference/cwinthread-class.md#m_pmainwnd) variable de miembro del objeto de aplicación. Una llamada a `OnFileNew` en el reemplazo del `InitInstance` función miembro de `CWinApp` establece *m_pMainWnd* para usted. Si no se llama `OnFileNew`, debe establecer el valor de la variable `InitInstance` usted mismo. (Las aplicaciones de componente (servidor) SDI COM no pueden establecer la variable si /Embedding se encuentra en la línea de comandos.) Tenga en cuenta que *m_pMainWnd* ahora es un miembro de clase `CWinThread` lugar `CWinApp`.

## <a name="see-also"></a>Vea también

[Las plantillas de documento y el proceso de creación de documento/vista](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Creación de plantillas de documentos](../mfc/document-template-creation.md)<br/>
[Crear documentos y vistas](../mfc/document-view-creation.md)<br/>
[Creación de nuevos documentos, ventanas y vistas](../mfc/creating-new-documents-windows-and-views.md)

