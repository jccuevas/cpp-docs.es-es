---
title: Administrar datos con Variables de datos de documentos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6ca7c673f47510282e129eab2538008400eb2fb9
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929437"
---
# <a name="managing-data-with-document-data-variables"></a>Administrar datos con variables de datos del documento
Implemente los datos del documento como variables de miembro de la clase de documento. Por ejemplo, el programa Scribble declara un miembro de datos de tipo `CObList` : una lista vinculada que almacena punteros a `CObject` objetos. Esta lista se utiliza para almacenar matrices de puntos que componen un dibujo de línea a mano alzada.  
  
 Cómo implementar los datos del documento miembro depende de la naturaleza de la aplicación. Para ayudarle a cabo, MFC proporciona un grupo de "clases de colección", matrices, listas y mapas (diccionarios), además de colecciones basadas en plantillas de C++, junto con las clases que encapsulan una variedad de tipos de datos comunes como `CString`, `CRect`, `CPoint`, `CSize`, y `CTime`. Para obtener más información sobre estas clases, consulte la [Class Library Overview](../mfc/class-library-overview.md) en el *referencia de MFC*.  
  
 Al definir los datos del documento miembro, normalmente agregará funciones de miembro a la clase de documento para establecer y obtener elementos de datos y realizar otras operaciones útiles sobre ellos.  
  
 Las vistas de acceso al objeto de documento mediante un puntero de la vista al documento, instalado en la vista en tiempo de creación. Puede recuperar un puntero this en funciones de miembro de una vista mediante una llamada a la `CView` función miembro `GetDocument`. No olvide convierte este puntero a su propio tipo de documento. A continuación, puede tener acceso a miembros públicos del documento a través del puntero.  
  
 Si la transferencia de datos frecuentes que requieren acceso directo, o que se va a usar a los miembros no públicos de la clase de documento, puede hacer que la vista de clase a friend (en términos de C++) de la clase de documento.  
  
## <a name="see-also"></a>Vea también  
 [Uso de documentos](../mfc/using-documents.md)

