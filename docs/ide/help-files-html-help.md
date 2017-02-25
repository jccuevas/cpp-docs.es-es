---
title: "Archivos de ayuda (Ayuda HTML) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tipos de archivo [C++], archivos de Ayuda HTML"
ms.assetid: d30a1b1b-318f-4a78-8b60-93da53a224a8
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Archivos de ayuda (Ayuda HTML)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si activa la casilla **Ayuda contextual** y selecciona **Formato de Ayuda HTML** en la página [Características avanzadas](../mfc/reference/advanced-features-mfc-application-wizard.md) del Asistente para aplicaciones MFC para agregar a la aplicación compatibilidad con Ayuda HTML, se crearán los siguientes archivos:  
  
|Nombre de archivo|Ubicación en el directorio|Ubicación en el Explorador de soluciones|Descripción|  
|-----------------------|--------------------------------|----------------------------------------------|-----------------|  
|*Nombre\_proyecto*.hhp|*Nombre\_proyecto*\\hlp|Archivos de Ayuda HTML|Archivo de proyecto de ayuda.  Contiene los datos necesarios para compilar los archivos de ayuda en un archivo .hxs file o .chm.|  
|*Nombre\_proyecto*.hhk|*Nombre\_proyecto*\\hlp|Archivos de Ayuda HTML|Contiene un índice de los temas de ayuda.|  
|*Nombre\_proyecto*.hhc|*Nombre\_proyecto*\\hlp|Archivos de Ayuda HTML|El contenido del proyecto de ayuda.|  
|Makehtmlhelp.bat|*Nombre\_proyecto*|Archivos de código fuente|Lo utiliza el sistema para generar el proyecto de Ayuda cuando se compila el proyecto.|  
|Afxcore.htm|*Nombre\_proyecto*\\hlp|Temas de Ayuda HTML|Contiene los temas de ayuda estándar para comandos y objetos de pantalla estándar de MFC.  Agregue sus propios temas de ayuda a este archivo.|  
|Afxprint.htm|*Nombre\_proyecto*\\hlp|Temas de Ayuda HTML|Contiene los temas de ayuda para los comandos de impresión.|  
|\*.jpg; \*.gif|*Nombre\_proyecto*\\hlp\\Images|Archivos de recursos|Contiene imágenes para los distintos temas de ayuda generados.|  
  
## Vea también  
 [Tipos de archivos creados para proyectos de Visual C\+\+](../ide/file-types-created-for-visual-cpp-projects.md)