---
title: Administrar datos con variables de datos del documento
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], data storage
- friend classes [MFC]
- classes [MFC], friend
- data [MFC]
- data [MFC], documents
- collection classes [MFC], used by document object
- document data [MFC]
- member variables [MFC], document class [MFC]
ms.assetid: e70b87f4-8c30-49e5-8986-521c2ff91704
ms.openlocfilehash: dc21bd4b3dbe7609a33af4b4f93f15a3f5c9a64e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259976"
---
# <a name="managing-data-with-document-data-variables"></a>Administrar datos con variables de datos del documento

Implemente los datos del documento como variables miembro de la clase de documento. Por ejemplo, el programa Scribble declara un miembro de datos de tipo `CObList` : una lista vinculada que almacena punteros a `CObject` objetos. Esta lista se usa para almacenar las matrices de puntos que componen un dibujo de línea a mano alzada.

Cómo implementar los datos del documento miembro depende de la naturaleza de la aplicación. Para ayudarle a horizontal, MFC proporciona un grupo de "clases de colección": las matrices, listas y mapas (diccionarios), incluidas las recopilaciones basadas en plantillas de C++, junto con las clases que encapsulan una variedad de tipos de datos comunes, como `CString`, `CRect`, `CPoint`, `CSize`, y `CTime`. Para obtener más información sobre estas clases, vea el [Class Library Overview](../mfc/class-library-overview.md) en el *referencia de MFC*.

Al definir los datos del documento miembro, normalmente agregará funciones de miembro a la clase de documento para establecer y obtener elementos de datos y realizar otras operaciones útiles en ellos.

Las vistas de acceso al objeto de documento mediante el uso de puntero de la vista en el documento, se instala en la vista en tiempo de creación. Puede recuperar el puntero this en funciones de miembro de una vista mediante una llamada a la `CView` función miembro `GetDocument`. No olvide convertir este puntero a su propio tipo de documento. A continuación, puede tener acceso a miembros públicos del documento a través del puntero.

Si la transferencia de datos frecuentes que requieren acceso directo, o desea usar a los miembros no públicos de la clase de documento, puede hacer que la vista clase a un amigo (en términos de C++) de la clase de documento.

## <a name="see-also"></a>Vea también

[Uso de documentos](../mfc/using-documents.md)
