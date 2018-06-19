---
title: Relaciones entre objetos MFC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, relationships between key objects
- objects [MFC], relationships
- relationships, MFC objects
- MFC object relationships
ms.assetid: 6e8f3b51-e80f-4d88-94c8-4c1e4ee163ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a0cdc4ebeab81a0eb69b96b161350f75ebc8b14
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379524"
---
# <a name="relationships-among-mfc-objects"></a>Relaciones entre objetos MFC
Con el fin de colocar el proceso de creación de documento/vista en perspectiva, considere la posibilidad de un programa en ejecución: un documento, la ventana de marco que se usa para contener la vista y la vista asociada con el documento.  
  
-   Un documento mantiene una lista de las vistas de ese documento y un puntero a la plantilla de documento que se creó el documento.  
  
-   Una vista mantiene un puntero a su documento y es un elemento secundario de su ventana de marco principal.  
  
-   Una ventana de marco de documento mantiene un puntero a su vista activa actual.  
  
-   Una plantilla de documento mantiene una lista de los documentos abiertos.  
  
-   La aplicación mantiene una lista de sus plantillas de documento.  
  
-   Windows realiza un seguimiento de todas las ventanas abiertas, por lo que puede enviar mensajes a ellos.  
  
 Estas relaciones se establecen durante la creación de documento/vista. En la tabla siguiente se muestra cómo los objetos en un programa en ejecución pueden tener acceso a otros objetos. Cualquier objeto puede obtener un puntero al objeto application mediante una llamada a la función global [AfxGetApp](../mfc/reference/application-information-and-management.md#afxgetapp).  
  
### <a name="gaining-access-to-other-objects-in-your-application"></a>Obtener acceso a otros objetos de la aplicación  
  
|Del objeto|Cómo obtener acceso a otros objetos|  
|-----------------|---------------------------------|  
|Documento|Use [GetFirstViewPosition](../mfc/reference/cdocument-class.md#getfirstviewposition) y [GetNextView](../mfc/reference/cdocument-class.md#getnextview) para tener acceso a la lista de vista del documento.<br /><br /> Llame a [GetDocTemplate](../mfc/reference/cdocument-class.md#getdoctemplate) para obtener la plantilla de documento.|  
|Ver|Llame a [GetDocument](../mfc/reference/cview-class.md#getdocument) para obtener el documento.<br /><br /> Llame a [GetParentFrame](../mfc/reference/cwnd-class.md#getparentframe) para obtener la ventana de marco.|  
|Ventana de marco de documento|Llame a [GetActiveView](../mfc/reference/cframewnd-class.md#getactiveview) para obtener la vista actual.<br /><br /> Llame a [GetActiveDocument](../mfc/reference/cframewnd-class.md#getactivedocument) para obtener el documento asociado a la vista actual.|  
|Ventana de marco MDI|Llame a [MDIGetActive](../mfc/reference/cmdiframewnd-class.md#mdigetactive) para obtener el activo actualmente [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md).|  
  
 Normalmente, una ventana de marco tiene una vista, pero a veces, como en las ventanas divisoras, la misma ventana de marco contiene varias vistas. La ventana de marco mantiene un puntero a la vista activa; el puntero se actualiza cada vez que se activa otra vista.  
  
> [!NOTE]
>  Un puntero a la ventana de marco principal se almacena en la [m_pMainWnd](../mfc/reference/cwinthread-class.md#m_pmainwnd) variable de miembro del objeto de aplicación. Una llamada a `OnFileNew` en la invalidación de la `InitInstance` función miembro de `CWinApp` establece `m_pMainWnd` para usted. Si no se llama `OnFileNew`, debe establecer el valor de la variable `InitInstance` usted mismo. (Las aplicaciones de componente (servidor) SDI COM no pueden establecer la variable si /Embedding se encuentra en la línea de comandos.) Tenga en cuenta que `m_pMainWnd` ahora es un miembro de clase `CWinThread` en lugar de `CWinApp`.  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de documento y el proceso de creación de documento/vista](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Creación de la plantilla de documento](../mfc/document-template-creation.md)   
 [Creación de documento/vista](../mfc/document-view-creation.md)   
 [Creación de nuevos documentos, ventanas y vistas](../mfc/creating-new-documents-windows-and-views.md)

