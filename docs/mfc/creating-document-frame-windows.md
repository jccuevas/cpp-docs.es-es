---
title: Crear ventanas de marco de documento | Documentos de Microsoft
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
- frame windows [MFC], creating
- document templates [MFC], and document frame windows
- windows [MFC], creating
- runtime, class information
- run-time class [MFC], and document frame window creation
- document frame windows [MFC], creating
- MFC, frame windows
ms.assetid: 8671e239-b76f-4dea-afa8-7024e6e58ff5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9098026c1a38f8e60093415ba1c5a2b3678b64d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="creating-document-frame-windows"></a>Crear ventanas de marco de documento
[Creación de documento/vista](../mfc/document-view-creation.md) muestra cómo el [CDocTemplate](../mfc/reference/cdoctemplate-class.md) objeto organiza la creación de la ventana de marco, el documento y la vista y conectándolos combina todas estas características. Tres [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) argumentos para el `CDocTemplate` constructor especifica las clases de vista que la plantilla de documento crea dinámicamente en respuesta a los comandos de usuario, como el comando nuevo en el archivo, documento y ventana de marco menú o el comando nueva ventana en un menú de ventana MDI. La plantilla de documento almacena esta información para su uso posterior cuando crea una ventana de marco para una vista y un documento.  
  
 Para el [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) mecanismo funcione correctamente, la derivada clases de ventana de marco deben declararse con el [DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) macro. Esto es porque el marco de trabajo necesita crear ventanas de marco mediante el mecanismo de construcción dinámica de clase de documento `CObject`.  
  
 Cuando el usuario elige un comando que crea un documento, el marco de trabajo llama a la plantilla de documento para crear el objeto de documento, su vista y la ventana de marco que se mostrará la vista. Cuando crea la ventana de marco de documento, la plantilla de documento crea un objeto de la clase apropiada, una clase derivada de [CFrameWnd](../mfc/reference/cframewnd-class.md) para una aplicación SDI o de [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) para formularios MDI aplicación. El marco de trabajo, a continuación, llama al objeto de ventana de marco [LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) función de miembro para obtener información para la creación de recursos y para crear la ventana de Windows. El marco de trabajo asocia el identificador de ventana para el objeto de ventana de marco. A continuación, crea la vista como una ventana secundaria de la ventana de marco de documento.  
  
 Tenga cuidado al decidir [cuándo se debe inicializar](../mfc/when-to-initialize-cwnd-objects.md) su `CWnd`-objeto derivado.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Derivar una clase de CObject (su mecanismo de creación dinámica)](../mfc/deriving-a-class-from-cobject.md)  
  
-   [Creación de documento/vista (plantillas y creación de ventana de marco)](../mfc/document-view-creation.md)  
  
-   [Destruir ventanas de marco](../mfc/destroying-frame-windows.md)  
  
## <a name="see-also"></a>Vea también  
 [Uso de ventanas de marco](../mfc/using-frame-windows.md)

