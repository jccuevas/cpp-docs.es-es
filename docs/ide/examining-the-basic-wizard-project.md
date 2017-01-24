---
title: "Examinar el proyecto b&#225;sico de asistente | Microsoft Docs"
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
  - "asistentes personalizados, archivos creados"
  - "asistentes personalizados, proyectos de asistente"
ms.assetid: c6423e3c-ddb0-43e0-b8e5-9e3a98a7908c
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Examinar el proyecto b&#225;sico de asistente
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Después de haber utilizado el [Asistente personalizado](../ide/creating-a-custom-wizard.md) para crear el proyecto básico, examine los archivos que éste ha creado.  
  
1.  En el **Explorador de soluciones**, expanda el proyecto y examine [los archivos](../ide/files-created-for-your-wizard.md) creados por el asistente.  
  
2.  Haga doble clic en el archivo Default.js para abrir el [archivo JScript](../ide/jscript-file.md) del proyecto en el editor de código.  Este archivo contiene funciones JScript que crean el proyecto cuando el usuario hace clic en el botón **Finalizar** del asistente.  Revise las funciones y los comentarios TODO de este archivo.  
  
3.  Si el proyecto tiene una interfaz de usuario, examine la carpeta [Archivos HTML](../ide/html-files.md) para comprobar si están todos los archivos .htm que especificó en la página [Configuración de la aplicación](../ide/application-settings-custom-wizard.md) del Asistente personalizado.  Haga doble clic en el archivo Default.htm para abrir la página HTML principal del proyecto en el [Diseñador HTML](../Topic/HTML%20Designer.md).  Tanto en la [Design View](../Topic/Design%20View1.md) como en la vista HTML, podrá ver el código HTML como [formato HTML](http://msdn.microsoft.com/es-es/7bb90672-b36a-4cf9-9bbc-677c9b956318).  Pase a la vista de formato HTML y revise el formato HTML.  Haga clic en el botón **Vista Sólo script** \(situado en la esquina superior derecha de la ventana de edición de la vista HTML, junto a la lista desplegable **Eventos**\) y examine el código JScript del archivo .htm.  De forma predeterminada, este archivo contiene las funciones de JScript que inicializan y cargan el asistente, y proporciona el comportamiento predeterminado de la interfaz **IVCWizCtrlUI**.  Vea el objeto <xref:Microsoft.VisualStudio.VsWizard.VCWizCtl> de coclase para obtener más información.  
  
4.  Guarde y cierre el proyecto del asistente.  
  
5.  Abra el cuadro de diálogo **Nuevo Proyecto** en Visual Studio y busque el icono del asistente.  Haga doble clic en el icono para abrir el asistente.  En él, podrá examinar las páginas básicas creadas por el Asistente personalizado.  Observe que la primera página contiene algunos controles HTML de ejemplo y los botones estándar **Finalizar**, **Cancelar** y **Ayuda**.  
  
6.  Haga clic en **Finalizar** para compilar un nuevo proyecto con el asistente.  De forma predeterminada, el asistente crea dos archivos de texto: ReadMe.txt y Sample.txt.  En estos archivos, se describe el proyecto creado por el asistente.  Cierre este proyecto y vuelva a abrir el proyecto del asistente.  
  
7.  Lea la sección [Examinar los aspectos prácticos de un asistente](../ide/examining-the-mechanics-of-a-wizard.md) para comprender mejor cómo el entorno de Visual Studio y el motor del Asistente para Visual C\+\+ generan el proyecto creado al ejecutar el asistente.  
  
 Ya puede empezar a [diseñar su asistente personalizado](../ide/customizing-your-wizard.md).  
  
## Vea también  
 [asistente personalizado](../ide/custom-wizard.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Pasos para diseñar un asistente](../ide/steps-to-designing-a-wizard.md)   
 [Archivos creados para un asistente](../ide/files-created-for-your-wizard.md)   
 [Proporcionar ayuda contextual](../ide/providing-context-sensitive-help.md)   
 [Personalizar un asistente](../ide/customizing-your-wizard.md)