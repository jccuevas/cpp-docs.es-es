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
ms.openlocfilehash: 04d9f2cf615636b151af93a3c3880f7357496048
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365275"
---
# <a name="wizards-and-the-resource-editors"></a>Asistentes y editores de recursos

Visual C++ incluye varios asistentes para su uso en la programación MFC, junto con muchos editores de recursos integrados. Para la programación de controles ActiveX, el [Asistente para controles ActiveX](../mfc/reference/mfc-activex-control-wizard.md) tiene un propósito muy similar al del Asistente para aplicaciones MFC. Aunque puede escribir aplicaciones MFC sin la mayoría de estas herramientas, las herramientas simplifican y aceleran enormemente su trabajo.

## <a name="use-the-mfc-application-wizard-to-create-an-mfc-application"></a><a name="_core_use_appwizard_to_create_an_mfc_application"></a>Utilice el Asistente para aplicaciones MFC para crear una aplicación MFC

Use el [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md) para crear un proyecto MFC en Visual C++, que puede incluir OLE y compatibilidad con bases de datos. Los archivos del proyecto contienen las clases de aplicación, documento, vista y ventana de marco; recursos estándar, incluidos los menús y una barra de herramientas opcional; otros archivos de Windows necesarios; y archivos .rtf opcionales que contienen temas estándar de la Ayuda de Windows que puede revisar y aumentar para crear el archivo de ayuda del programa.

## <a name="use-class-view-to-manage-classes-and-windows-messages"></a><a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a>Usar la vista de clases para administrar clases y mensajes de Windows

Vista de clases le ayuda a crear funciones de controlador para mensajes y comandos de Windows, crear y administrar clases, crear variables miembro de clase, crear métodos y propiedades de automatización, crear clases de base de datos y mucho más.

> [!NOTE]
> La vista de clases también le ayuda a invalidar las funciones virtuales en las clases MFC. Seleccione la clase y la función virtual que desea invalidar. El resto del proceso es similar al control de mensajes, como se describe en los párrafos siguientes.

Las aplicaciones que se ejecutan en Windows están [controladas por mensajes.](../mfc/message-handling-and-mapping.md) Las acciones del usuario y otros eventos que se producen en el programa en ejecución hacen que Windows envíe mensajes a las ventanas del programa. Por ejemplo, si el usuario hace clic en el mouse en una ventana, Windows envía un mensaje de WM_LBUTTONDOWN cuando se presiona el botón izquierdo del mouse y un WM_LBUTTONUP mensaje cuando se suelta el botón. Windows también envía mensajes WM_COMMAND cuando el usuario selecciona comandos de la barra de menús.

En el marco de trabajo MFC, varios objetos, como documentos, vistas, ventanas de marco, plantillas de documento y el objeto de aplicación, pueden "controlar" mensajes. Este tipo de objeto proporciona una "función de controlador" como una de sus funciones miembro y el marco de trabajo asigna el mensaje entrante a su controlador.

Una gran parte de la tarea de programación es elegir qué mensajes asignar a qué objetos y, a continuación, implementar esa asignación. Para ello, utilice la vista de clases y el [Asistente para clases](reference/mfc-class-wizard.md).

El [Asistente para clases](reference/mfc-class-wizard.md) creará funciones miembro de controlador de mensajes vacías y usará el editor de código fuente para implementar el cuerpo del controlador. También puede crear o editar clases (incluidas las clases propias, no derivadas de clases MFC) y sus miembros con la vista de clases. Para obtener más información sobre el uso de la vista de clases y sobre los asistentes que agregan código a un proyecto, vea [Agregar funcionalidad con asistentes](../ide/adding-functionality-with-code-wizards-cpp.md)de código .

## <a name="use-the-resource-editors-to-create-and-edit-resources"></a><a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a>Utilice los editores de recursos para crear y editar recursos

Utilice los editores de recursos de Visual C++ para crear y editar [menús,](../windows/resource-editors.md) cuadros de diálogo, controles personalizados, teclas de aceleración, mapas de bits, iconos, cursores, cadenas y recursos de versión. A partir de Visual C++ versión 4.0, un editor de barras de herramientas facilita mucho la creación de barras de herramientas.

Para ayudarle aún más, la biblioteca Microsoft Foundation Class proporciona un archivo denominado COMMON. RES, que contiene recursos de "clip art" que puede copiar de COMMON. RES y pegar en su propio archivo de recursos. Común. RES incluye botones de barra de herramientas, cursores comunes, iconos y mucho más. Puede usar, modificar y redistribuir estos recursos en la aplicación. Para obtener más información acerca de COMMON. RES, consulte el [ejemplo de imágenes prediseñadas](../overview/visual-cpp-samples.md).

El Asistente para aplicaciones MFC, los asistentes de Visual C++, los editores de recursos y el marco de trabajo MFC realizan mucho trabajo y facilitan mucho la administración del código. La mayor parte del código específico de la aplicación se encuentra en las clases de documento y vista.

## <a name="see-also"></a>Consulte también

[Uso de las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
