---
title: "Asistente para aplicaciones Win32 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.win32.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para aplicaciones Win32"
  - "Asistente para proyectos Win32"
ms.assetid: 5d7b3a5e-8461-479a-969a-67b7883725b9
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Asistente para aplicaciones Win32
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El Asistentes para aplicaciones Win32 de Visual C\+\+ permite crear cuatro tipos de proyecto \(que se muestran en los encabezados de la tabla siguiente\). En cada caso, puede especificar opciones adicionales apropiadas para el tipo de proyecto que abra. En la tabla siguiente se indican las opciones disponibles para cada tipo de aplicación.  
  
|Tipo de soporte|Aplicación de consola|Aplicación ejecutable \(para Windows\)|Biblioteca de vínculos dinámicos|Biblioteca estática|  
|---------------------|---------------------------|--------------------------------------------|--------------------------------------|-------------------------|  
|**Proyecto vacío**|Sí|Sí|Sí|No|  
|**Exportar símbolos**|No|No|Sí|No|  
|**Encabezado precompilado**|No|No|No|Sí|  
|**compatibilidad con ATL**|Sí|No|No|No|  
|**compatibilidad con MFC**|Sí|No|No|Sí|  
  
## Información general  
 En esta página del asistente se describe la configuración del proyecto actual para la aplicación Win32 que se está creando. De forma predeterminada, se establecen las siguientes opciones:  
  
-   El proyecto es una aplicación para Windows.  
  
-   El proyecto no está vacío.  
  
-   El proyecto no contiene símbolos para exportar.  
  
-   El proyecto no usa un archivo de encabezado precompilado \(esta opción solo está disponible para proyectos de biblioteca estática\).  
  
-   El proyecto no incluye compatibilidad con MFC ni con ATL.  
  
 Para cambiar estos valores predeterminados, haga clic en la pestaña [Configuración de la aplicación](../Topic/Application%20Settings,%20Win%2032%20Project%20Wizard.md), en la columna izquierda del asistente, y haga los cambios que desee.  
  
 Una vez creada una aplicación de escritorio de Windows, puede agregar clases C\+\+ genéricas mediante el Asistente para código [genérico](../ide/generic-cpp-class-wizard.md). Puede agregar otros elementos, como archivos HTML, archivos de encabezado, recursos o archivos de texto.  
  
> [!NOTE]
>  No es posible agregar clases ATL y solo pueden agregarse clases MFC en los tipos de aplicación de escritorio de Windows que sean compatibles con MFC \(vea la tabla anterior\).  
  
 Puede ver los archivos que el asistente crea para el proyecto en el **Explorador de soluciones**. Para obtener más información sobre los archivos que crea el asistente para el proyecto, vea el archivo Readme.txt generado por el proyecto. Para obtener más información sobre los tipos de archivo, consulte [Tipos de archivo creados para proyectos de Visual C\+\+](../ide/file-types-created-for-visual-cpp-projects.md).  
  
## Vea también  
 [Crear una aplicación de escritorio de Windows vacía](../windows/creating-an-empty-windows-desktop-application.md)   
 [Tipos de proyecto de Visual C\+\+](../ide/visual-cpp-project-types.md)