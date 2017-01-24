---
title: "Archivos de recursos (C++) | Microsoft Docs"
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
  - "tipos de archivo [C++], archivos de recursos"
  - "archivos de recursos"
  - "recursos [C++]"
ms.assetid: 338a4a0f-0c62-4ef1-a34f-5d86262d93a4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Archivos de recursos (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los recursos son elementos de interfaz que proporcionan información al usuario.  Los mapas de bits, los iconos, las barras de herramientas y los cursores son recursos.  Es posible manipular algunos recursos para realizar una acción como seleccionar de un menú o escribir datos en un cuadro de diálogo.  
  
 Vea [Trabajar con recursos](../mfc/working-with-resource-files.md) para obtener más información.  
  
|Nombre de archivo|Ubicación en el directorio|Ubicación en el Explorador de soluciones|Descripción|  
|-----------------------|--------------------------------|----------------------------------------------|-----------------|  
|*Nombre\_proyecto*.rc|*Nombre\_proyecto*|Archivos de código fuente|Archivo de script de recursos para el proyecto.  Contendrá lo siguiente, en función del tipo de proyecto y la compatibilidad seleccionada para el mismo \(por ejemplo, barras de herramientas, cuadros de diálogo o HTML\):<br /><br /> -   Definición de menú predeterminada.<br />-   Tablas de cadenas y de aceleradores.<br />-   Cuadro de diálogo **Acerca de** predeterminado.<br />-   Otros cuadros de diálogo.<br />-   Archivo de icono \(res\\*Nombre\_proyecto*.ico\).<br />-   Información de la versión.<br />-   Mapas de bits.<br />-   Barra de herramientas.<br />-   Archivos HTML.<br /><br /> El archivo de recursos incluye el archivo Afxres.rc para recursos estándar de Microsoft Foundation Class.|  
|Resource.h|*Nombre\_proyecto*|Archivos de encabezado|Archivo de encabezado de recursos que incluye definiciones para los recursos utilizados por el proyecto.|  
|*Nombre\_proyecto*.rc2|*Nombre\_proyecto*\\res|Archivos de código fuente|Archivo de script que contiene recursos adicionales utilizados por el proyecto.  Puede incluir el archivo .rc2 en el nivel superior del archivo .rc del proyecto.<br /><br /> Un archivo .rc2 resulta útil para incluir recursos utilizados por varios proyectos diferentes.  En lugar de tener que crear los mismos recursos varias veces para proyectos diferentes, puede colocarlos en un archivo .rc2 e incluir el archivo .rc2 en el archivo .rc principal.|  
|*Nombre\_proyecto*.def|*Nombre\_proyecto*|Archivos de código fuente|Archivo de definición de módulo para un proyecto DLL.  Para un control, proporciona el nombre y la descripción del mismo, así como el tamaño del montón en tiempo de ejecución.|  
|*Nombre\_proyecto*.ico|*Nombre\_proyecto*\\res|Archivos de recursos|Archivo de icono para el proyecto o control.  Este icono aparece cuando se minimiza la aplicación.  También se utiliza en el cuadro **Acerca de** de la aplicación.  De manera predeterminada, MFC proporciona el icono MFC y ATL proporciona el icono ATL.|  
|*Nombre\_proyecto*.ico|*Nombre\_proyecto*\\res|Archivos de recursos|Archivo de icono para un proyecto MFC que incluya compatibilidad con la arquitectura documento\/vista.|  
|Toolbar.bmp|*Nombre\_proyecto*\\res|Archivos de recursos|Archivo de mapa de bits que representa la aplicación o el control en una barra de herramientas o una paleta.  Este mapa de bits se incluye en el archivo de recursos del proyecto.  La barra de herramientas inicial y la barra de estado se crean en la clase **CMainFrame**.|  
|ribbon.mfcribbon\-ms|*Nombre\_proyecto*\\res|Archivos de recursos|Archivo de recursos que contiene el código XML que define los botones, controles y atributos de la cinta de opciones.  Para obtener más información, vea [Diseñador de la cinta de opciones \(MFC\)](../mfc/ribbon-designer-mfc.md).|  
  
## Vea también  
 [Tipos de archivos creados para proyectos de Visual C\+\+](../ide/file-types-created-for-visual-cpp-projects.md)