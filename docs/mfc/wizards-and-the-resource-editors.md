---
title: "Asistentes y editores de recursos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asistentes para aplicaciones [C++], y MFC"
  - "Vista de clases (herramienta), administrar mensajes de Windows"
  - "editores, recurso"
  - "MFC [C++], editores de recursos"
  - "MFC [C++], controles wizard"
  - "Asistente para aplicaciones MFC"
  - "editores de recursos, MFC"
  - "asistentes [C++], programación en MFC"
  - "asistentes [MFC]"
ms.assetid: f5dd4d13-9dc1-4a49-b6bf-5b3cb45fa8ba
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Asistentes y editores de recursos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ incluye varios asistentes para el uso en MFC que programa, junto con muchos editores de recursos integrados.  Para la programación de controles ActiveX, [Asistente para controles ActiveX](../mfc/reference/mfc-activex-control-wizard.md) tiene una finalidad como el del asistente para aplicaciones MFC.  Aunque puede escribir aplicaciones MFC sin la mayoría de estas herramientas, las herramientas simplifican considerablemente y progreso del trabajo.  
  
##  <a name="_core_use_appwizard_to_create_an_mfc_application"></a> Utilice el asistente para crear una aplicación MFC  
 Utilice [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md) para crear un proyecto MFC en Visual C\+\+, que pueden incluir OLE y compatibilidad con bases de datos.  Los archivos del proyecto contienen la aplicación, el documento, la vista, y las clases de la cuadro\- ventana; recursos estándar, incluyendo menús y una barra de herramientas opcional; otros archivos necesarios de Windows; y archivos opcionales .rtf que contienen temas de ayuda de Windows estándar que puede revisar y aumentar para crear el archivo de ayuda del programa.  
  
##  <a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a> Vista de clases de uso para administrar clases y los mensajes de Windows  
 Ayuda de la vista de clases puede crear funciones controladoras para los mensajes y los comandos de Windows, crea y administra clases, crea variables miembro de clase, crea métodos de automatización y propiedades, crean clases de base de datos, y más.  
  
> [!NOTE]
>  De la clase de la vista ayuda también permite reemplazar funciones virtuales en las clases MFC.  Seleccione la clase y la función virtual para reemplazar.  El resto del proceso es similar al control de mensajes, como se describe en los párrafos siguientes.  
  
 Las aplicaciones que se ejecutan en Windows son [mensaje controlado](../mfc/message-handling-and-mapping.md).  Las acciones del usuario y otros eventos que aparecen en la causa Windows del programa en ejecución de enviar mensajes a las ventanas del programa.  Por ejemplo, si el usuario hace clic con el mouse en una ventana, Windows envía un mensaje de `WM_LBUTTONDOWN` cuando se presiona el botón primario y un mensaje de `WM_LBUTTONUP` cuando se suelta el botón.  Windows también envía los mensajes de **WM\_COMMAND** cuando el usuario selecciona comandos de la barra de menús.  
  
 En el marco de trabajo de MFC, varios objetos, como documentos, vistas, ventanas de marco, plantillas de documento, y el objeto application, pueden “controlar” mensajes.  Este objeto proporciona una “función controladora” mientras se trabaja una del miembro, y el marco asigna el mensaje entrante al controlador.  
  
 Una gran parte de la tarea de programación está eligiendo que los mensajes para asignar a qué objetos a continuación implementar esa asignación.  Para ello, utilice la vista de clases y la ventana Propiedades.  
  
 La ventana Propiedades creará funciones vacías del miembro del controlador de mensajes, y utiliza el editor de código fuente para implementar el cuerpo del controlador.  También puede crear o editar clases \(incluidas las clases de propietario, no derivadas de clases MFC\) y sus miembros con la vista de clases.  Para obtener más información sobre cómo utilizar la vista de clases y los asistentes que agregan código a un proyecto, vea [Agregar funcionalidad con los asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md).  
  
##  <a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a> Usar los editores de recursos para crear y modificar recursos  
 Utilice Visual C\+\+ [editores de recursos](../mfc/resource-editors.md) para crear y modificar los menús, cuadros de diálogo, los controles personalizados, teclas de aceleración, mapas de bits, iconos, cursores, cadenas, y recursos de la versión.  A partir de la versión 4.0 de Visual C\+\+, un editor de barras de herramientas crea crear barras de herramientas mucho más fácil.  
  
 Para ayudarle aún más, la biblioteca Microsoft Foundation Class proporciona un archivo denominado COMMON.RES, que contiene recursos de “clipart” que puede copiar de COMMON.RES y pegar en poseer el archivo de recursos.  COMMON.RES incluye botones de la barra de herramientas, cursores comunes, los iconos, y más.  Puede utilizar, modificar, y redistribuir estos recursos en la aplicación.  Para obtener más información sobre COMMON.RES, vea [Ejemplo de imágenes prediseñadas](../top/visual-cpp-samples.md).  
  
 El asistente para aplicaciones MFC, los asistentes de Visual C\+\+, los editores de recursos, y el marco de trabajo de MFC hacen mucho trabajo automáticamente y se crean controlando el código mucho más fácil.  La mayor parte del código específico de la aplicación está en las clases de documento y de la vista.  
  
## Vea también  
 [Usar las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)