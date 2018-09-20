---
title: Creación de documento marco Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 172076113a6bd7e223d99c238d0e05987cdcaae6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433704"
---
# <a name="creating-document-frame-windows"></a>Crear ventanas de marco de documento

[Creación de documento/vista](../mfc/document-view-creation.md) muestra cómo el [CDocTemplate](../mfc/reference/cdoctemplate-class.md) objeto organiza la creación de la ventana de marco, el documento y la vista y conectarlos todos juntos. Tres [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) argumentos para el `CDocTemplate` constructor especifica la ventana de marco, documento y las clases de vistas que crea la plantilla de documento de forma dinámica en respuesta a los comandos de usuario, como el nuevo comando en el archivo menú o el comando nueva ventana en un menú de la ventana MDI. La plantilla de documento almacena esta información para su uso posterior cuando crea una ventana de marco para una vista y un documento.

Para el [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) mecanismo funcione correctamente, la derivada clases de ventana de marco se deben declarar con la [DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) macro. Esto es porque el marco de trabajo necesita para crear ventanas de marco mediante el mecanismo de construcción dinámica de clase de documento `CObject`.

Cuando el usuario elige un comando que crea un documento, el marco de trabajo llama a la plantilla de documento para crear el objeto de documento, su vista y la ventana de marco que se mostrará la vista. Cuando crea la ventana de marco de documento, la plantilla de documento crea un objeto de la clase apropiada, una clase derivada de [CFrameWnd](../mfc/reference/cframewnd-class.md) para una aplicación SDI o de [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) para formularios MDI aplicación. El marco llama a continuación, el objeto de ventana de marco [LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) función de miembro para obtener información sobre la creación de recursos y crear la ventana de Windows. El marco de trabajo asocia el identificador de ventana para el objeto de ventana de marco. A continuación, crea la vista como una ventana secundaria de la ventana de marco de documento.

Tenga cuidado al decidir [cuándo se debe inicializar](../mfc/when-to-initialize-cwnd-objects.md) su `CWnd`-objeto derivado.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Derivar una clase de CObject (su mecanismo de creación dinámica)](../mfc/deriving-a-class-from-cobject.md)

- [Creación de documentos y vistas (plantillas y creación de la ventana de marco)](../mfc/document-view-creation.md)

- [Destruir ventanas de marco](../mfc/destroying-frame-windows.md)

## <a name="see-also"></a>Vea también

[Uso de ventanas de marco](../mfc/using-frame-windows.md)

