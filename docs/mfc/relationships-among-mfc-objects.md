---
title: Relaciones entre objetos MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, relationships between key objects
- objects [MFC], relationships
- relationships, MFC objects
- MFC object relationships
ms.assetid: 6e8f3b51-e80f-4d88-94c8-4c1e4ee163ad
ms.openlocfilehash: d7e40e25b405d3f8ec50a518889cc2b89bc8c725
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372809"
---
# <a name="relationships-among-mfc-objects"></a>Relaciones entre objetos MFC

Para ayudar a poner el proceso de creación de documento/vista en perspectiva, considere un programa en ejecución: un documento, la ventana de marco utilizada para contener la vista y la vista asociada al documento.

- Un documento mantiene una lista de las vistas de ese documento y un puntero a la plantilla de documento que creó el documento.

- Una vista mantiene un puntero a su documento y es un elemento secundario de su ventana de marco primario.

- Una ventana de marco de documento mantiene un puntero a su vista activa actual.

- Una plantilla de documento mantiene una lista de sus documentos abiertos.

- La aplicación mantiene una lista de sus plantillas de documento.

- Windows realiza un seguimiento de todas las ventanas abiertas para que pueda enviarles mensajes.

Estas relaciones se establecen durante la creación de documentos/vistas. En la tabla siguiente se muestra cómo los objetos de un programa en ejecución pueden acceder a otros objetos. Cualquier objeto puede obtener un puntero al objeto de aplicación llamando a la función global [AfxGetApp](../mfc/reference/application-information-and-management.md#afxgetapp).

### <a name="gaining-access-to-other-objects-in-your-application"></a>Obtener acceso a otros objetos en su aplicación

|Desde el objeto|Cómo acceder a otros objetos|
|-----------------|---------------------------------|
|Documento|Utilice [GetFirstViewPosition](../mfc/reference/cdocument-class.md#getfirstviewposition) y [GetNextView](../mfc/reference/cdocument-class.md#getnextview) para tener acceso a la lista de vistas del documento.<br /><br /> Llame a [GetDocTemplate](../mfc/reference/cdocument-class.md#getdoctemplate) para obtener la plantilla de documento.|
|Ver|Llame a [GetDocument](../mfc/reference/cview-class.md#getdocument) para obtener el documento.<br /><br /> Llame a [GetParentFrame](../mfc/reference/cwnd-class.md#getparentframe) para obtener la ventana de marco.|
|Ventana de marco de documento|Llame a [GetActiveView](../mfc/reference/cframewnd-class.md#getactiveview) para obtener la vista actual.<br /><br /> Llame a [GetActiveDocument](../mfc/reference/cframewnd-class.md#getactivedocument) para obtener el documento adjunto a la vista actual.|
|Ventana de marco MDI|Llame a [MDIGetActive](../mfc/reference/cmdiframewnd-class.md#mdigetactive) para obtener el [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)actualmente activo .|

Normalmente, una ventana de marco tiene una vista, pero a veces, como en las ventanas divisoras, la misma ventana de marco contiene varias vistas. La ventana de marco mantiene un puntero a la vista activa actualmente; el puntero se actualiza en cualquier momento que se activa otra vista.

> [!NOTE]
> Un puntero a la ventana de marco principal se almacena en el [m_pMainWnd](../mfc/reference/cwinthread-class.md#m_pmainwnd) variable miembro del objeto de aplicación. Una llamada `OnFileNew` a la `InitInstance` invalidación `CWinApp` de la función miembro de conjuntos *m_pMainWnd* para usted. Si no llama `OnFileNew`a , debe establecer el `InitInstance` valor de la variable en usted mismo. (Es posible que las aplicaciones del componente COM (servidor) De SDI no establezcan la variable si /Embedding está en la línea de comandos.) Tenga *m_pMainWnd* en cuenta que m_pMainWnd `CWinThread` ahora `CWinApp`es miembro de la clase en lugar de .

## <a name="see-also"></a>Consulte también

[Plantillas de documento y el proceso de creación de documentos/vistas](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Creación de plantillas de documentos](../mfc/document-template-creation.md)<br/>
[Crear documentos y vistas](../mfc/document-view-creation.md)<br/>
[Crear nuevos documentos, ventanas y vistas](../mfc/creating-new-documents-windows-and-views.md)
