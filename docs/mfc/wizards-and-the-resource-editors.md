---
title: Asistentes y editores de recursos
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [MFC], and MFC
- MFC, resource editors
- resource editors, MFC
- MFC Application Wizard
- editors [MFC], resource
- wizards [MFC]
- wizards [MFC], MFC programming
- MFC, wizards
- Class View tool, managing Windows messages
ms.assetid: f5dd4d13-9dc1-4a49-b6bf-5b3cb45fa8ba
ms.openlocfilehash: fb1a523ca82cd8e1a4256da657efe9702517beda
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907351"
---
# <a name="wizards-and-the-resource-editors"></a>Asistentes y editores de recursos

Visual C++ incluye varios asistentes que se usan en la programación de MFC, junto con muchos editores de recursos integrados. En la programación de controles ActiveX, el Asistente para controles [ActiveX](../mfc/reference/mfc-activex-control-wizard.md) sirve de forma similar a la del Asistente para aplicaciones MFC. Aunque puede escribir aplicaciones MFC sin la mayoría de estas herramientas, las herramientas simplifican y agilizan enormemente el trabajo.

##  <a name="_core_use_appwizard_to_create_an_mfc_application"></a>Usar el Asistente para aplicaciones MFC para crear una aplicación MFC

Use el [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md) para crear un proyecto MFC en C++visual, que puede incluir compatibilidad con bases de datos y OLE. Los archivos del proyecto contienen las clases de aplicación, documento, vista y ventana de marco. recursos estándar, incluidos los menús y una barra de herramientas opcional; Otros archivos necesarios de Windows; y archivos. rtf opcionales que contienen temas de ayuda de Windows estándar que puede revisar y aumentar para crear el archivo de ayuda del programa.

##  <a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a>Usar Vista de clases para administrar clases y mensajes de Windows

Vista de clases ayuda a crear funciones de controlador para mensajes y comandos de Windows, crear y administrar clases, crear variables de miembro de clase, crear métodos y propiedades de automatización, crear clases de base de datos, etc.

> [!NOTE]
>  Vista de clases también ayuda a invalidar funciones virtuales en las clases MFC. Seleccione la clase y la función virtual que se va a invalidar. El resto del proceso es similar al control de mensajes, tal y como se describe en los párrafos siguientes.

Las aplicaciones que se ejecutan en Windows están [controladas por mensajes](../mfc/message-handling-and-mapping.md). Las acciones del usuario y otros eventos que se producen en el programa en ejecución hacen que Windows envíe mensajes a las ventanas del programa. Por ejemplo, si el usuario hace clic con el mouse en una ventana, Windows envía un mensaje de WM_LBUTTONDOWN cuando se presiona el botón primario del mouse y un mensaje de WM_LBUTTONUP cuando se suelta el botón. Windows también envía mensajes WM_COMMAND cuando el usuario selecciona comandos en la barra de menús.

En el marco de trabajo de MFC, varios objetos, como documentos, vistas, ventanas de marco, plantillas de documento y el objeto de aplicación, pueden "controlar" los mensajes. Este tipo de objeto proporciona una "función controladora" como una de sus funciones miembro y el marco de trabajo asigna el mensaje entrante a su controlador.

Una gran parte de la tarea de programación es elegir qué mensajes se deben asignar a qué objetos y, a continuación, implementar esa asignación. Para ello, use Vista de clases y el [Asistente para clases](reference/mfc-class-wizard.md).

El [Asistente para clases](reference/mfc-class-wizard.md) creará funciones de miembro de controlador de mensajes vacías y utilizará el editor de código fuente para implementar el cuerpo del controlador. También puede crear o editar clases (incluidas clases propias, no derivadas de clases MFC) y sus miembros con Vista de clases. Para obtener más información sobre el uso de Vista de clases y sobre los asistentes que agregan código a un proyecto, vea [Agregar funcionalidad con los asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md).

##  <a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a>Usar los editores de recursos para crear y editar recursos

Use los C++ [editores de recursos](../windows/resource-editors.md) visuales para crear y editar menús, cuadros de diálogo, controles personalizados, teclas de aceleración, mapas de bits, iconos, cursores, cadenas y recursos de versión. A partir de C++ la versión 4,0 de Visual, un editor de barras de herramientas facilita enormemente la creación de barras de herramientas.

Para que le resulte más fácil, el biblioteca MFC proporciona un archivo llamado COMMON. RES, que contiene los recursos de "imagen prediseñada" que puede copiar de común. RES y péguelo en su propio archivo de recursos. Normal. RES incluye botones de barra de herramientas, cursores comunes, iconos, etc. Puede usar, modificar y redistribuir estos recursos en la aplicación. Para obtener más información acerca de COMMON. RES, vea el [ejemplo de clipart](../overview/visual-cpp-samples.md).

El Asistente para aplicaciones MFC, los C++ asistentes visuales, los editores de recursos y el marco de trabajo de MFC hacen mucho trabajo por usted y facilitan la administración del código. La mayor parte del código específico de la aplicación se encuentra en las clases de documento y vista.

## <a name="see-also"></a>Vea también

[Uso de las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
