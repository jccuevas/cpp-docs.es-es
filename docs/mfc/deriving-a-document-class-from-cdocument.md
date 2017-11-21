---
title: Derivar una clase de documento de CDocument | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CDocument class [MFC], deriving from
- classes [MFC], deriving from CDocument
- document objects [MFC], derived
- derived classes [MFC], functions often overridden
- document classes [MFC], functions often overridden
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8f9152384522725dc932d0ce5e1c4cc81827160b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="deriving-a-document-class-from-cdocument"></a>Derivar una clase de documento de CDocument
Documentos contienen y administran los datos de aplicación. Para utilizar la clase de documento proporcionada por el Asistente para aplicaciones MFC, debe hacer lo siguiente:  
  
-   Derivar una clase de **CDocument** para cada tipo de documento.  
  
-   Agregue variables miembro para almacenar datos de cada documento.  
  
-   Invalidar **CDocument**del `Serialize` función miembro en la clase de documento. `Serialize`escribe y lee los datos del documento hacia y desde el disco.  
  
## <a name="other-document-functions-often-overridden"></a>Otras funciones de documento que se reemplazan con frecuencia  
 También puede invalidar otros **CDocument** funciones miembro. En concreto, a menudo necesitará invalidar [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) y [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) para inicializar los miembros de datos del documento y [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) destruir asigna datos de forma dinámica. Para obtener información acerca de los miembros reemplazables, vea la clase [CDocument](../mfc/reference/cdocument-class.md) en el *referencia de MFC*.  
  
## <a name="see-also"></a>Vea también  
 [Uso de documentos](../mfc/using-documents.md)

