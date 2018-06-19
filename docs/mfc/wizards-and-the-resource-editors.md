---
title: Asistentes y editores de recursos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 33fb1caa496c34111de133a113433a614ff5eb22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383846"
---
# <a name="wizards-and-the-resource-editors"></a>Asistentes y editores de recursos
Visual C++ incluye a varios asistentes para su uso en la programación de MFC, junto con muchos editores de recursos integrados. La programación, los controles ActiveX la [Asistente para controles ActiveX](../mfc/reference/mfc-activex-control-wizard.md) sirve para un propósito similar a la que el Asistente para aplicaciones MFC. Aunque puede escribir aplicaciones MFC sin usar la mayoría de estas herramientas, las herramientas en gran medida simplificarán y acelerar su trabajo.  
  
##  <a name="_core_use_appwizard_to_create_an_mfc_application"></a> Usar al Asistente para aplicaciones MFC para crear una aplicación MFC  
 Use la [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md) para crear un proyecto MFC en Visual C++, que puede incluir OLE y compatibilidad con la base de datos. Archivos de proyecto contienen su aplicación, documento, vista y las clases de ventana de marco; recursos estándar, incluidos los menús y una barra de herramientas opcional; otros archivos de Windows; que necesita y archivos .rtf opcionales que contienen temas de Ayuda de Windows estándar que se pueden revisar y ampliar para crear el archivo de Ayuda del programa.  
  
##  <a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a> Usar la vista de clases para administrar clases y mensajes de Windows  
 Clase vista le ayuda a crea funciones de controlador de mensajes de Windows y los comandos, crea y administrar clases, crear variables de miembro de clase, crear propiedades y métodos de automatización, crear clases de base de datos y mucho más.  
  
> [!NOTE]
>  Vista de clases también ayuda a reemplazar funciones virtuales en las clases MFC. Seleccione la clase y la función virtual que desea reemplazar. El resto del proceso es similar al control de mensajes, como se describe en los párrafos siguientes.  
  
 Son aplicaciones que se ejecutan en Windows [controladas por mensajes](../mfc/message-handling-and-mapping.md). Las acciones del usuario y otros eventos que se producen en el programa en ejecución hacen que Windows enviar mensajes a las ventanas en el programa. Por ejemplo, si el usuario hace clic en el mouse en una ventana, Windows envía una `WM_LBUTTONDOWN` mensaje cuando se presiona el botón primario del mouse y un `WM_LBUTTONUP` el mensaje cuando se suelta el botón. Windows también envía **WM_COMMAND** mensajes cuando el usuario selecciona comandos en la barra de menús.  
  
 En el marco de trabajo MFC, varios objetos, como documentos, vistas, ventanas de marco, plantillas de documento y el objeto de aplicación, pueden "controlar" mensajes. Este tipo de objeto proporciona una función de controlador"" como uno de sus miembros, funciones y el marco de trabajo asigna el mensaje entrante a su controlador.  
  
 Gran parte de la tarea de programación es elegir qué mensajes se asignan a los objetos y, a continuación, implementar dicha asignación. Para ello, utilice la vista de clases y la ventana Propiedades.  
  
 La ventana Propiedades creará funciones miembro de controlador de mensajes vacía y utilizar el editor de código fuente para implementar el cuerpo del controlador. También puede crear o editar clases (incluidas las clases de su elección, que no se deriva de las clases MFC) y sus miembros con vista de clases. Para obtener más información sobre el uso de la vista de clases y los asistentes que agregan código a un proyecto, vea [agregar funcionalidad con los asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md).  
  
##  <a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a> Utilice los editores de recursos para crear y editar recursos  
 Usar Visual C++ [editores de recursos](../windows/resource-editors.md) para crear y editar menús, cuadros de diálogo, controles personalizados, teclas de aceleración, mapas de bits, iconos, cursores, cadenas y recursos de la versión. A partir de la versión 4.0 de Visual C++, un editor de la barra de herramientas facilita la creación de barras al.  
  
 Para ayudar a aún más, la biblioteca Microsoft Foundation Class proporciona un archivo denominado común. RES, que contiene los recursos de "imágenes prediseñadas" que puede copiar desde comunes. RES y pegar en su propio archivo de recursos. COMÚN. RES incluye botones de barra de herramientas, comunes cursores, iconos y mucho más. Puede utilizar, modificar y redistribuir estos recursos en la aplicación. Para obtener más información sobre COMMON. ¡RES, vea el [Clipart (ejemplo)](../visual-cpp-samples.md).  
  
 El Asistente para aplicaciones MFC, los asistentes de Visual C++, editores de recursos y el marco de trabajo MFC hacer mucho trabajo por usted y facilitan la administración de su código mucho más fácil. La mayor parte del código específico de la aplicación está en las clases de documento y vista.  
  
## <a name="see-also"></a>Vea también  
 [Uso de las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
