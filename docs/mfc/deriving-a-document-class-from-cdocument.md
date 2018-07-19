---
title: Derivar una clase de documento de CDocument | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CDocument class [MFC], deriving from
- classes [MFC], deriving from CDocument
- document objects [MFC], derived
- derived classes [MFC], functions often overridden
- document classes [MFC], functions often overridden
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a81f3c3a36f049e3f47401efa31b36677b3b9ba6
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931754"
---
# <a name="deriving-a-document-class-from-cdocument"></a>Derivar una clase de documento de CDocument
Documentos contienen y administran los datos de aplicación. Para utilizar la clase de documento proporcionada por el Asistente para aplicaciones MFC, debe hacer lo siguiente:  
  
-   Derivar una clase de `CDocument` para cada tipo de documento.  
  
-   Agregue variables miembro para almacenar datos de cada documento.  
  
-   Invalidar `CDocument`del `Serialize` función miembro en la clase de documento. `Serialize` escribe y lee los datos del documento hacia y desde el disco.  
  
## <a name="other-document-functions-often-overridden"></a>Otras funciones de documento que se reemplazan con frecuencia  
 También puede invalidar otros `CDocument` funciones miembro. En concreto, a menudo necesitará invalidar [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) y [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) para inicializar los miembros de datos del documento y [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) destruir asigna datos de forma dinámica. Para obtener información acerca de los miembros reemplazables, vea la clase [CDocument](../mfc/reference/cdocument-class.md) en el *referencia de MFC*.  
  
## <a name="see-also"></a>Vea también  
 [Uso de documentos](../mfc/using-documents.md)

