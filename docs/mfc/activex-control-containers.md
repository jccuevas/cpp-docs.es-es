---
title: Contenedores de controles ActiveX
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX control containers [MFC]
- OLE controls [MFC], containers
ms.assetid: 0eb1a713-e607-4c79-a0c7-67c5f1fd5fab
ms.openlocfilehash: 42fa18c41ebd960aa8de080df00556ad5c909d40
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620758"
---
# <a name="activex-control-containers"></a>Contenedores de controles ActiveX

Un contenedor de controles ActiveX es un contenedor que es totalmente compatible con los controles ActiveX y puede incorporarlos en sus propias ventanas o cuadros de diálogo. Un control ActiveX es un elemento de software reutilizable que puede usar en muchos proyectos de desarrollo. Los controles permiten al usuario de la aplicación tener acceso a las bases de datos, supervisar los datos y hacer varias selecciones dentro de las aplicaciones. Para obtener más información sobre los controles ActiveX, vea el artículo [controles ActiveX MFC](mfc-activex-controls.md).

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información, vea [controles ActiveX](activex-controls.md).

Los contenedores de control suelen tomar dos formas en un proyecto:

- Cuadros de diálogo y ventanas similares a los cuadros de diálogo, como las vistas de formulario, donde se usa un control ActiveX en alguna parte del cuadro de diálogo.

- Windows en una aplicación, donde se usa un control ActiveX en una barra de herramientas u otra ubicación de la ventana de usuario.

El contenedor de controles ActiveX interactúa con el control a través de [los métodos](mfc-activex-controls-methods.md) y [propiedades](mfc-activex-controls-properties.md)expuestos. A estos métodos y propiedades, a los que se puede tener acceso y modificar mediante el contenedor de controles, se obtiene acceso a través de una clase contenedora en el proyecto de contenedor de controles ActiveX. El control ActiveX incrustado también puede interactuar con el contenedor mediante la activación (envío) de [eventos](mfc-activex-controls-events.md) para notificar al contenedor que se ha producido una acción. El contenedor de control puede optar por actuar sobre estas notificaciones o no.

En otros artículos se describen varios temas, desde la creación de un proyecto de contenedor de controles ActiveX hasta problemas de implementación básicos relacionados con los contenedores de controles ActiveX creados con Visual C++:

- [Crear un contenedor de controles ActiveX MFC](reference/creating-an-mfc-activex-control-container.md)

- [Contenedores de controles ActiveX](containers-for-activex-controls.md)

- [Contenedores de controles ActiveX: Habilitar manualmente la contención de controles ActiveX](activex-control-containers-manually-enabling-activex-control-containment.md)

- [Contenedores de controles ActiveX: Insertar un control en una aplicación de contenedor de controles](inserting-a-control-into-a-control-container-application.md)

- [Contenedores de controles ActiveX: Conectar un control ActiveX a una variable de miembro](activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)

- [Contenedores de controles ActiveX: controlar eventos desde un control ActiveX](activex-control-containers-handling-events-from-an-activex-control.md)

- [Contenedores de controles ActiveX: Ver y modificar propiedades de los controles](activex-control-containers-viewing-and-modifying-control-properties.md)

- [Contenedores de controles ActiveX: Programar controles ActiveX en un contenedor de controles ActiveX](programming-activex-controls-in-a-activex-control-container.md)

- [Contenedores de controles ActiveX: Usar controles en un contenedor sin cuadro de diálogo](activex-control-containers-using-controls-in-a-non-dialog-container.md)

Para obtener más información sobre el uso de controles ActiveX en un cuadro de diálogo, vea los temas del [Editor de cuadros de diálogo](../windows/dialog-editor.md) .

Para obtener una lista de los artículos en los que se explican los detalles del desarrollo de controles ActiveX mediante Visual C++ y las clases de controles ActiveX de MFC, vea [controles ActiveX MFC](mfc-activex-controls.md). Los artículos se agrupan por categorías funcionales.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)
