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
ms.openlocfilehash: 3d845b0fc3d00369d44c21c04a3fb7e3b8d6189e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618326"
---
# <a name="managing-data-with-document-data-variables"></a>Administrar datos con variables de datos del documento

Implemente los datos del documento como variables de miembro de la clase de documento. Por ejemplo, el programa Scribble declara un miembro de datos de tipo `CObList` , una lista vinculada que almacena punteros a `CObject` objetos. Esta lista se utiliza para almacenar matrices de puntos que componen un dibujo de línea a mano alzada.

La forma de implementar los datos de los miembros del documento depende de la naturaleza de la aplicación. Para ayudarle, MFC proporciona un grupo de "clases de colección": matrices, listas y mapas (diccionarios), incluidas las colecciones basadas en plantillas de C++, junto con las clases que encapsulan una variedad de tipos de datos comunes, como `CString` , `CRect` , `CPoint` , `CSize` y `CTime` . Para obtener más información sobre estas clases, vea la [información general](class-library-overview.md) de la biblioteca de clases en la *referencia de MFC*.

Cuando se definen los datos de miembro del documento, normalmente se agregan funciones miembro a la clase de documento para establecer y obtener elementos de datos, así como para realizar otras operaciones útiles en ellos.

Las vistas tienen acceso al objeto de documento mediante el puntero de la vista al documento, instalado en la vista en el momento de su creación. Puede recuperar este puntero en las funciones miembro de una vista mediante una llamada a la `CView` función miembro `GetDocument` . Asegúrese de convertir este puntero a su propio tipo de documento. A continuación, puede tener acceso a los miembros del documento público a través del puntero.

Si la transferencia de datos frecuente requiere acceso directo o desea usar los miembros no públicos de la clase de documento, es posible que desee convertir la clase de vista en un amigo (en términos de C++) de la clase de documento.

## <a name="see-also"></a>Consulte también

[Usar documentos](using-documents.md)
