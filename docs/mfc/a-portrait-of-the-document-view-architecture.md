---
title: Un retrato de la arquitectura de vista-documento | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- documents [MFC], views
- multiple views [MFC], updating from document
- document/view architecture [MFC]
- views [MFC], and user input
- documents [MFC], accessing data from view
- views [MFC], updating
- input [MFC], view class
- documents [MFC], multiple views
- document/view architecture [MFC], accessing data from view
- document/view architecture [MFC], about document/view architecture
- views [MFC], accessing document data from
ms.assetid: 4e7f65dc-b166-45d8-bcd5-9bb0d399b946
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d366cf7c9aee6988d715edbe30e3938c30557e2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329821"
---
# <a name="a-portrait-of-the-documentview-architecture"></a>Un retrato de la arquitectura documento/vista
En una aplicación típica de MFC están emparejadas de documentos y vistas. Datos se almacenan en el documento, pero la vista tiene privilegios de acceso a los datos. La separación del documento de vista separa el almacenamiento y el mantenimiento de datos de su presentación.  
  
## <a name="gaining-access-to-document-data-from-the-view"></a>Obtener acceso a datos de la vista del documento  
 La vista tiene acceso a datos de su documento con la [GetDocument](../mfc/reference/cview-class.md#getdocument) funcione, que devuelve un puntero al documento, o mediante la realización de la vista de clases C++ `friend` de la clase de documento. A continuación, la vista utiliza su acceso a los datos para obtener los datos cuando esté listo para dibujar o manipularlos en caso contrario.  
  
 Por ejemplo, desde la vista [OnDraw](../mfc/reference/cview-class.md#ondraw) función miembro, la vista utiliza **GetDocument** para obtener un puntero al documento. A continuación, utiliza ese puntero para tener acceso a un `CString` miembro de datos en el documento. La vista pasa la cadena a la `TextOut` (función). Para ver el código de este ejemplo, vea [dibujar en una vista](../mfc/drawing-in-a-view.md).  
  
## <a name="user-input-to-the-view"></a>Proporcionados por el usuario a la vista  
 La vista también podría interpretar un clic del mouse dentro de sí mismo como selección o edición de los datos. Del mismo modo, se podrían interpretar pulsaciones de teclas como entrada de datos o de edición. Suponga que el usuario escribe una cadena en una vista que administra el texto. La vista obtiene un puntero al documento y usa el puntero para pasar los nuevos datos al documento, que almacena en alguna estructura de datos.  
  
## <a name="updating-multiple-views-of-the-same-document"></a>Actualización de varias vistas del mismo documento  
 En una aplicación con varias vistas del mismo documento, como una ventana divisora en un editor de texto, la vista pasa primero los nuevos datos al documento. A continuación, llama el documento [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) función miembro, lo que indica todas las vistas del documento para actualizar por sí mismos, que refleja los nuevos datos. Esto sincroniza las vistas.  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Ventajas de la arquitectura documento/vista](../mfc/advantages-of-the-document-view-architecture.md)  
  
-   [Alternativas a la arquitectura documento/vista](../mfc/alternatives-to-the-document-view-architecture.md)  
  
## <a name="see-also"></a>Vea también  
 [Arquitectura documento/vista](../mfc/document-view-architecture.md)

