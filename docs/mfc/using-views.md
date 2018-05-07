---
title: Usar vistas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interacting with users and role of view class [MFC]
- drawing [MFC], data
- rendering data
- view classes [MFC], role in managing user interaction
- CView class [MFC], view architecture
- MFC, views
- views [MFC], using
- painting data
- user input [MFC], interpreting through view class [MFC]
- view classes [MFC], role in displaying application data
ms.assetid: dc3de6ad-5c64-4317-8f10-8bdcc38cdbd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4094f41f00266b229c755232f534e9c35d29fe7a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="using-views"></a>Usar vistas
Son las responsabilidades de la vista para mostrar gráficamente los datos del documento al usuario para que acepte e interpretar proporcionados por el usuario que las operaciones en el documento. Las tareas para escribir la clase de vista son:  
  
-   Escribir la clase de vista [OnDraw](../mfc/reference/cview-class.md#ondraw) función de miembro, que representa los datos del documento.  
  
-   Conecte los mensajes de Windows apropiados y objetos de interfaz de usuario como elementos de menú para funciones de miembro de controlador de mensajes en la clase de vista.  
  
-   Implementar esos controladores para interpretar proporcionados por el usuario.  
  
 Además, debe invalidar otros `CView` las funciones miembro de la clase de vista derivada. En concreto, quizás desee reemplazar [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) para realizar la inicialización especial para la vista y [OnUpdate](../mfc/reference/cview-class.md#onupdate) para realizar cualquier procesamiento especial necesario justo antes de que la vista vuelve a dibujarse automáticamente. Para documentos de varias páginas, también debe invalidar [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) para inicializar el cuadro de diálogo de impresión con el número de páginas que desea imprimir y otra información. Para obtener más información sobre cómo reemplazar `CView` funciones miembro, vea la clase [CView](../mfc/reference/cview-class.md) en el *referencia de MFC*.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Clases de vista derivadas disponibles en MFC](../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [Dibujar en una vista](../mfc/drawing-in-a-view.md)  
  
-   [Interpretar la entrada del usuario a través de una vista](../mfc/interpreting-user-input-through-a-view.md)  
  
-   [El rol de la vista en la impresión](../mfc/role-of-the-view-in-printing.md)  
  
-   [Desplazar y escalar vistas](../mfc/scrolling-and-scaling-views.md)  
  
-   [Inicializar y limpiar documentos y vistas](../mfc/initializing-and-cleaning-up-documents-and-views.md)  
  
## <a name="see-also"></a>Vea también  
 [Arquitectura documento/vista](../mfc/document-view-architecture.md)   
 [Clase CFormView](../mfc/reference/cformview-class.md)   
 [Vistas de registros (acceso a datos MFC)](../data/record-views-mfc-data-access.md)   
 [Omisión del mecanismo de serialización](../mfc/bypassing-the-serialization-mechanism.md)

