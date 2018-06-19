---
title: Inicializar documentos y vistas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializing documents [MFC]
- documents [MFC], initializing
- views [MFC], initializing
- initializing objects [MFC], document objects
- initializing views [MFC]
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e46d130f535076c2591101ab57423db1130ef749
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348054"
---
# <a name="initializing-documents-and-views"></a>Inicializar documentos y vistas
Se crean documentos de dos maneras diferentes, por lo que la clase de documento debe ser compatible con ambos modos. En primer lugar, el usuario puede crear un nuevo documento vacío con el comando archivo nuevo. En ese caso, inicialice el documento en el reemplazo de la [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) función miembro de clase [CDocument](../mfc/reference/cdocument-class.md). En segundo lugar, el usuario puede utilizar el comando Abrir en el menú archivo para crear un nuevo documento cuyo contenido se lee desde un archivo. En ese caso, inicialice el documento en el reemplazo de la [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) función miembro de clase **CDocument**. Si ambos inicializaciones son iguales, puede llamar a una función miembro común desde ambos reemplazos, o `OnOpenDocument` puede llamar a `OnNewDocument` para inicializar un documento limpio y, a continuación, finalizar la operación de apertura.  
  
 Las vistas se crean una vez creados los documentos. El mejor momento para inicializar una vista es después de que el marco de trabajo ha terminado de crear el documento, la ventana de marco y la vista. Puede inicializar la vista invalidando el [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) función miembro de [CView](../mfc/reference/cview-class.md). Si necesita reinicializar o ajustar algo cada vez que los cambios en el documento, puede invalidar [OnUpdate](../mfc/reference/cview-class.md#onupdate).  
  
## <a name="see-also"></a>Vea también  
 [Inicialización y limpieza de documentos y vistas](../mfc/initializing-and-cleaning-up-documents-and-views.md)

