---
title: Administrar datos con Variables de datos de documentos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c737557d503ca7e0959d159a0818f1ca78280ea2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="managing-data-with-document-data-variables"></a>Administrar datos con variables de datos del documento
Implemente los datos del documento como variables de miembro de la clase de documento. Por ejemplo, el programa Scribble declara un miembro de datos de tipo `CObList` : una lista vinculada que almacena punteros a `CObject` objetos. Esta lista se utiliza para almacenar matrices de puntos que componen un dibujo de línea a mano alzada.  
  
 Cómo implementar los datos del documento miembro depende de la naturaleza de la aplicación. Para ayudarle a cabo, MFC proporciona un grupo de "clases de colección", matrices, listas y mapas (diccionarios), además de colecciones basadas en plantillas de C++, junto con las clases que encapsulan una variedad de tipos de datos comunes como `CString`, `CRect`, `CPoint`, `CSize`, y `CTime`. Para obtener más información sobre estas clases, consulte la [Class Library Overview](../mfc/class-library-overview.md) en el *referencia de MFC*.  
  
 Al definir los datos del documento miembro, normalmente agregará funciones de miembro a la clase de documento para establecer y obtener elementos de datos y realizar otras operaciones útiles sobre ellos.  
  
 Las vistas de acceso al objeto de documento mediante un puntero de la vista al documento, instalado en la vista en tiempo de creación. Puede recuperar un puntero this en funciones de miembro de una vista mediante una llamada a la `CView` función miembro **GetDocument**. No olvide convierte este puntero a su propio tipo de documento. Then you can access public document members through the pointer.  
  
 If frequent data transfer requires direct access, or you wish to use the nonpublic members of the document class, you may want to make your view class a friend (in C++ terms) of the document class.  
  
## <a name="see-also"></a>Vea también  
 [Uso de documentos](../mfc/using-documents.md)

