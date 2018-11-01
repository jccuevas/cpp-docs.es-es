---
title: Contenedores de controles ActiveX
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX control containers [MFC]
- OLE controls [MFC], containers
ms.assetid: 0eb1a713-e607-4c79-a0c7-67c5f1fd5fab
ms.openlocfilehash: 3356c5d94eaf4cef0b44c509144d0de4a5d42abf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549122"
---
# <a name="activex-control-containers"></a>Contenedores de controles ActiveX

Un contenedor de controles ActiveX es un contenedor que es totalmente compatible con los controles ActiveX y puede incorporarlos a sus propias ventanas o cuadros de diálogo. Un control ActiveX es un elemento de software reutilizable que puede usar en muchos proyectos de desarrollo. Controles permiten a los usuarios de su aplicación tener acceso a las bases de datos, supervisar los datos y realizar varias selecciones dentro de sus aplicaciones. Para obtener más información sobre los controles ActiveX, vea el artículo [controles ActiveX MFC](../mfc/mfc-activex-controls.md).

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no se recomienda para nuevo desarrollo. Para obtener más información, consulte [controles ActiveX](activex-controls.md).

Contenedores de controles suelen tener dos formas en un proyecto:

- Cuadro de diálogo ventanas como vistas de formulario, donde se usa en algún lugar un control ActiveX en el cuadro de diálogo y cuadros de diálogo.

- Windows en una aplicación, donde un control ActiveX se utiliza en una barra de herramientas o en otra ubicación en la ventana de usuario.

Expone el contenedor del control interactúa con el control a través de ActiveX [métodos](../mfc/mfc-activex-controls-methods.md) y [propiedades](../mfc/mfc-activex-controls-properties.md). Estos métodos y propiedades, que pueden acceder y modificar el contenedor de control, se accede a través de una clase de contenedor en el proyecto de contenedor de controles ActiveX. El control ActiveX incrustado también puede interactuar con el contenedor activando (enviar) [eventos](../mfc/mfc-activex-controls-events.md) para notificar al contenedor que se ha producido una acción. Puede elegir el contenedor del control actuar en estas notificaciones o no.

Otros artículos explican varios temas, desde la creación de un proyecto de contenedor del control ActiveX a aspectos básicos de implementación relacionados con los contenedores de control ActiveX creados con Visual C++:

- [Creación de un contenedor de controles ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control-container.md)

- [Contenedores de controles ActiveX](../mfc/containers-for-activex-controls.md)

- [Contenedores de controles ActiveX: Habilitar manualmente la contención de controles ActiveX](../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)

- [Contenedores de controles ActiveX: Insertar un control en una aplicación de contenedor de controles](../mfc/inserting-a-control-into-a-control-container-application.md)

- [Contenedores de controles ActiveX: Conectar un control ActiveX a una variable de miembro](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)

- [Contenedores de controles ActiveX: Controlar el control de eventos de un control ActiveX](../mfc/activex-control-containers-handling-events-from-an-activex-control.md)

- [Contenedores de controles ActiveX: Ver y modificar propiedades de los controles](../mfc/activex-control-containers-viewing-and-modifying-control-properties.md)

- [Contenedores de controles ActiveX: Programar controles ActiveX en un contenedor de controles ActiveX](../mfc/programming-activex-controls-in-a-activex-control-container.md)

- [Contenedores de controles ActiveX: Usar controles en un contenedor sin cuadro de diálogo](../mfc/activex-control-containers-using-controls-in-a-non-dialog-container.md)

Para obtener más información sobre el uso de controles ActiveX en un cuadro de diálogo, vea el [Editor de cuadro de diálogo](../windows/dialog-editor.md) temas.

Para obtener una lista de artículos que explican los detalles de desarrollo de controles ActiveX utilizando Visual C++ y las clases de controles ActiveX de MFC, vea [controles ActiveX MFC](../mfc/mfc-activex-controls.md). Los artículos se agrupan por categorías funcionales.

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

