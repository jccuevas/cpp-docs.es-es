---
title: Un retrato de la arquitectura de documentos y vistas
ms.date: 11/04/2016
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
ms.openlocfilehash: f0e71c42004b5409eeb6f5e2ddabd33296cf5f49
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623447"
---
# <a name="a-portrait-of-the-documentview-architecture"></a>Un retrato de la arquitectura documento/vista

Los documentos y las vistas se emparejan en una aplicación MFC típica. Los datos se almacenan en el documento, pero la vista tiene privilegios de acceso a los datos. La separación del documento de la vista separa el almacenamiento y el mantenimiento de los datos de la pantalla.

## <a name="gaining-access-to-document-data-from-the-view"></a>Obtener acceso a los datos de documento desde la vista

La vista obtiene acceso a los datos de su documento con la función [getdocument](reference/cview-class.md#getdocument) , que devuelve un puntero al documento, o haciendo que la clase de vista sea un C++ `friend` de la clase de documento. A continuación, la vista utiliza su acceso a los datos para obtener los datos cuando está listo para dibujarlos o manipularlos de otro modo.

Por ejemplo, desde la función miembro [OnDraw](reference/cview-class.md#ondraw) de la vista, la vista utiliza `GetDocument` para obtener un puntero de documento. A continuación, utiliza ese puntero para tener acceso a un `CString` miembro de datos del documento. La vista pasa la cadena a la `TextOut` función. Para ver el código de este ejemplo, vea [dibujar en una vista](drawing-in-a-view.md).

## <a name="user-input-to-the-view"></a>Datos proporcionados por el usuario a la vista

La vista también puede interpretar un clic del mouse en sí mismo como selección o edición de datos. Del mismo modo, puede interpretar las pulsaciones de teclas como entrada o edición de datos. Supongamos que el usuario escribe una cadena en una vista que administra el texto. La vista obtiene un puntero al documento y usa el puntero para pasar los nuevos datos al documento, que los almacena en una estructura de datos.

## <a name="updating-multiple-views-of-the-same-document"></a>Actualizar varias vistas del mismo documento

En una aplicación con varias vistas del mismo documento, como una ventana divisora en un editor de texto, la vista pasa primero los nuevos datos al documento. A continuación, llama a la función miembro [UpdateAllViews](reference/cdocument-class.md#updateallviews) del documento, que indica a todas las vistas del documento que se actualicen, reflejando los datos nuevos. Esto sincroniza las vistas.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Ventajas de la arquitectura documento/vista](advantages-of-the-document-view-architecture.md)

- [Alternativas a la arquitectura documento/vista](alternatives-to-the-document-view-architecture.md)

## <a name="see-also"></a>Consulte también

[Arquitectura documento/vista](document-view-architecture.md)
