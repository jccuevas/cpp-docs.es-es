---
title: "Archivos de ayuda (WinHelp) | Microsoft Docs"
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
  - "tipos de archivo [C++], WinHelp (archivos)"
ms.assetid: 4fdcbd66-66b0-4866-894a-fd7b4c2557e4
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Archivos de ayuda (WinHelp)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si activa la casilla **Ayuda contextual** y selecciona **Formato WinHelp** en la página [Características avanzadas](../mfc/reference/advanced-features-mfc-application-wizard.md) del Asistente para aplicaciones MFC para agregar a la aplicación compatibilidad con ayuda de tipo WinHelp, se crearán los siguientes archivos:  
  
|Nombre de archivo|Ubicación en el directorio|Ubicación en el Explorador de soluciones|Descripción|  
|-----------------------|--------------------------------|----------------------------------------------|-----------------|  
|*Nombre\_proyecto*.hpj|*Nombre\_proyecto*\\hlp|Archivos de código fuente|Archivo de proyecto de Ayuda utilizado por el compilador de Ayudas para crear el archivo de Ayuda del programa o control.|  
|*Nombre\_proyecto*.rtf|*Nombre\_proyecto*\\hlp|Archivos de Ayuda|Contiene temas plantilla que puede editar e información acerca de la personalización del archivo .hpj.|  
|*Nombre\_proyecto*.cnt|*Nombre\_proyecto*\\hlp|Archivos de Ayuda|Proporciona la estructura de la ventana **Contenido** de la Ayuda de Windows.|  
|Makehelp.bat|*Nombre\_proyecto*|Archivos de código fuente|Lo utiliza el sistema para generar el proyecto de Ayuda cuando se compila el proyecto.|  
|Print.rtf|*Nombre\_proyecto*\\hlp|Archivos de Ayuda|Se crea si el proyecto incluye compatibilidad con la impresión \(la incluye de forma predeterminada\).  Describe los comandos y los cuadros de diálogo de impresión.|  
|\*.bmp|*Nombre\_proyecto*\\hlp|Archivos de recursos|Contiene imágenes para los distintos temas de ayuda generados.|  
  
 Puede agregar compatibilidad con WinHelp a un proyecto de control ActiveX MFC seleccionando **Generar archivos de ayuda** en la ficha [Configuración de la aplicación](../mfc/reference/application-settings-mfc-activex-control-wizard.md) del Asistente para controles ActiveX MFC.  Al agregar compatibilidad con ayudas a un control ActiveX MFC, se agregarán al proyecto los siguientes archivos:  
  
|Nombre de archivo|Ubicación en el directorio|Ubicación en el Explorador de soluciones|Descripción|  
|-----------------------|--------------------------------|----------------------------------------------|-----------------|  
|*Nombre\_proyecto*.hpj|*Nombre\_proyecto*\\hlp|Archivos de código fuente|Archivo de proyecto utilizado por el compilador de Ayudas para crear el archivo de Ayuda del programa o control.|  
|*Nombre\_proyecto*.rtf|*Nombre\_proyecto*\\hlp|Proyecto|Contiene temas plantilla que puede editar e información acerca de la personalización del archivo .hpj.|  
|Makehelp.bat|*Nombre\_proyecto*|Archivos de código fuente|Lo utiliza el sistema para generar el proyecto de Ayuda cuando se compila el proyecto.|  
|Bullet.bmp|*Nombre\_proyecto*|Archivos de recursos|Lo utilizan temas de archivo de Ayuda estándar para representar listas con viñetas.|  
  
## Vea también  
 [Tipos de archivos creados para proyectos de Visual C\+\+](../ide/file-types-created-for-visual-cpp-projects.md)