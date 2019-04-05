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
ms.openlocfilehash: 41cbb86b4245bd78baecd222b5573ba5e877243a
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "58773832"
---
# <a name="wizards-and-the-resource-editors"></a>Asistentes y editores de recursos

Visual C++ incluye a varios asistentes para su uso en la programación de MFC, junto con muchos editores de recursos integrados. Programación, los controles ActiveX la [Asistente para controles ActiveX](../mfc/reference/mfc-activex-control-wizard.md) tiene una finalidad similar a la que el Asistente para aplicaciones MFC. Aunque puede escribir aplicaciones MFC sin la mayoría de estas herramientas, las herramientas en gran medida simplifican y acelerar su trabajo.

##  <a name="_core_use_appwizard_to_create_an_mfc_application"></a> Usar al Asistente para aplicaciones MFC para crear una aplicación MFC

Use la [MFC Application Wizard](../mfc/reference/mfc-application-wizard.md) para crear un proyecto MFC en Visual C++, que puede incluir OLE y compatibilidad con la base de datos. Los archivos del proyecto contienen su aplicación, documento, vista y las clases de ventana de marco; recursos estándar, incluidos los menús y una barra de herramientas opcional; otros archivos de Windows; que necesita y archivos .rtf opcional que contiene temas de Ayuda de Windows estándar que se pueden revisar y ampliar para crear el archivo de Ayuda del programa.

##  <a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a> Utilice la vista de clases para administrar las clases y los mensajes de Windows

Clase vista le ayuda a crear las funciones de controlador de comandos y mensajes de Windows, crear y administrar clases, cree variables miembro de clase, crear propiedades y métodos de automatización, crear clases de base de datos y mucho más.

> [!NOTE]
>  Vista de clases también le ayuda a reemplazar funciones virtuales en las clases MFC. Seleccione la clase y la función virtual a invalidar. El resto del proceso es similar al control de mensajes, como se describe en los párrafos siguientes.

Las aplicaciones que se ejecutan en Windows son [controladas por mensajes](../mfc/message-handling-and-mapping.md). Las acciones del usuario y otros eventos que se producen en el programa en ejecución que Windows enviar mensajes a las ventanas en el programa. Por ejemplo, si el usuario hace clic en el mouse en una ventana, Windows envía un mensaje WM_LBUTTONDOWN cuando se presiona el botón primario del mouse y un mensaje WM_LBUTTONUP cuando se suelta el botón. Windows también envía mensajes WM_COMMAND cuando el usuario selecciona comandos en la barra de menús.

En el marco de trabajo MFC, varios objetos, como documentos, vistas, ventanas de marco, las plantillas de documento y el objeto de aplicación, pueden "handle" los mensajes. Este tipo de objeto proporciona una función de controlador"" como uno de sus miembros, funciones y el marco asigna el mensaje entrante a su controlador.

Gran parte de la tarea de programación es elegir qué mensajes se asignan a los objetos y, a continuación, implementar esa asignación. Para ello, utilice la vista de clases y la ventana Propiedades.

La ventana Propiedades creará funciones miembro de controlador de mensaje vacío y utilizar el editor de código fuente para implementar el cuerpo del controlador. También puede crear o editar clases (incluidas sus propias clases, no derivadas de clases MFC) y sus miembros con vista de clases. Para obtener más información sobre el uso de la vista de clases y los asistentes que agregan código a un proyecto, vea [agregar funcionalidad con los asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md).

##  <a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a> Utilice los editores de recursos para crear y editar recursos

Utilice Visual C++ [editores de recursos](../windows/resource-editors.md) para crear y editar menús, cuadros de diálogo, controles personalizados, teclas de aceleración, mapas de bits, iconos, cursores, cadenas y recursos de la versión. A partir de la versión 4.0 de Visual C++, un editor de la barra de herramientas facilita la creación de barras.

Para facilitar aún más, la biblioteca Microsoft Foundation Class proporciona un archivo denominado común. RES, que contiene los recursos de "imágenes prediseñadas" que se pueden copiar desde comunes. RES y pegar en su propio archivo de recursos. COMUNES. RES incluye botones de barra de herramientas común cursores, iconos y mucho más. Puede utilizar, modificar y redistribuir estos recursos en la aplicación. Para obtener más información sobre COMMON. RES, vea el [ejemplo Clipart](../overview/visual-cpp-samples.md).

El marco de trabajo MFC, editores de recursos, los asistentes de Visual C++ y MFC Application Wizard hacer mucho trabajo por usted y facilitan la administración de su código mucho más fácil. La mayor parte del código específico de la aplicación está en las clases de documento y vista.

## <a name="see-also"></a>Vea también

[Usar las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
