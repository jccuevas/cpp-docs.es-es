---
title: Crear ventanas de marco de documento
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], creating
- document templates [MFC], and document frame windows
- windows [MFC], creating
- runtime, class information
- run-time class [MFC], and document frame window creation
- document frame windows [MFC], creating
- MFC, frame windows
ms.assetid: 8671e239-b76f-4dea-afa8-7024e6e58ff5
ms.openlocfilehash: e15a2a6bc016bf23bc0decf529b4c3ffeecc3a4c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621945"
---
# <a name="creating-document-frame-windows"></a>Crear ventanas de marco de documento

La [creación de documentos y vistas](document-view-creation.md) muestra cómo el objeto [CDocTemplate](reference/cdoctemplate-class.md) orquesta la creación de la ventana de marco, el documento y la vista, y cómo conectarlos todos juntos. Tres argumentos [CRuntimeClass](reference/cruntimeclass-structure.md) para el `CDocTemplate` constructor especifican las clases de ventana de marco, documento y vista que la plantilla de documento crea dinámicamente en respuesta a comandos de usuario, como el nuevo comando en el menú archivo o el comando nueva ventana en un menú de ventana MDI. La plantilla de documento almacena esta información para su uso posterior cuando crea una ventana de marco para una vista y un documento.

Para que el mecanismo de [RUNTIME_CLASS](reference/run-time-object-model-services.md#runtime_class) funcione correctamente, las clases derivadas de la ventana de marco se deben declarar con la macro [DECLARE_DYNCREATE](reference/run-time-object-model-services.md#declare_dyncreate) . Esto se debe a que el marco debe crear ventanas de marco de documento mediante el mecanismo de construcción dinámica de la clase `CObject` .

Cuando el usuario elige un comando que crea un documento, el marco de trabajo llama a la plantilla de documento para crear el objeto de documento, su vista y la ventana de marco que mostrará la vista. Al crear la ventana de marco de documento, la plantilla de documento crea un objeto de la clase adecuada, una clase derivada de [CFrameWnd](reference/cframewnd-class.md) para una aplicación SDI o de [CMDIChildWnd](reference/cmdichildwnd-class.md) para una aplicación MDI. A continuación, el marco de trabajo llama a la función miembro [LoadFrame](reference/cframewnd-class.md#loadframe) del objeto de la ventana de marco para obtener información de creación de los recursos y para crear la ventana de Windows. El marco de trabajo asocia el identificador de ventana al objeto de ventana de marco. A continuación, crea la vista como una ventana secundaria de la ventana de marco del documento.

Tenga cuidado a la hora de decidir [Cuándo inicializar](when-to-initialize-cwnd-objects.md) el `CWnd` objeto derivado de.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Derivar una clase de CObject (su mecanismo de creación dinámico)](deriving-a-class-from-cobject.md)

- [Creación de documentos y vistas (plantillas y creación de ventanas de marco)](document-view-creation.md)

- [Destrucción de ventanas de marco](destroying-frame-windows.md)

## <a name="see-also"></a>Consulte también

[Usar ventanas de marco](using-frame-windows.md)
