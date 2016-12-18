---
title: "Compatibilidad del asistente con otros idiomas | Microsoft Docs"
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
  - "vc.appwiz.EastAsianLanguages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "compatibilidad de lenguaje para proyectos MFC"
  - "proyectos [C++], compatibilidad con el idioma"
  - "asistentes [C++], compatibilidad con el idioma"
ms.assetid: b653c673-0687-455c-885f-15d7e2f4149d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Compatibilidad del asistente con otros idiomas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al instalar Visual Studio, la aplicación de instalación detecta la configuración regional definida en el sistema e instala las plantillas de idioma apropiadas para esa configuración regional.  Por ejemplo, para configuraciones regionales de Europa Occidental, el programa de instalación instala Inglés, Francés, Italiano, Español y Alemán.  Estos idiomas aparecen en la lista **Idioma de los recursos** de la página [Tipo de aplicación](../mfc/reference/application-type-mfc-application-wizard.md) del Asistente para aplicaciones MFC.  
  
## Plantillas de idioma  
 No se instalarán todas las plantillas en todos los sistemas, ya que las plantillas son básicamente codificación ANSI, y no todos los recursos se pueden editar en todos los sistemas.  Por ejemplo, de manera predeterminada, no podrá editar en un sistema en francés recursos en japonés.  
  
 Si utiliza Windows 2000 o una versión posterior, y desea crear una aplicación MFC en otro idioma, deberá copiar en el sistema el directorio de la plantilla para ese idioma desde el disco de instalación de Visual Studio \(Disco 1\).  
  
> [!NOTE]
>  Para modificar el proyecto creado, debe establecer como configuración regional del sistema la correspondiente al idioma seleccionado.  
  
 A cada plantilla se le asigna una carpeta en el directorio \\Microsoft Visual Studio .NET 2003\\Vc7\\VCWizards\\mfcappwiz\\templates\\, como se indica en la tabla siguiente.  Para tener acceso a la plantilla de idioma que desee, copie la carpeta apropiada al directorio \\mfcappwiz\\templates\\ del equipo.  Cuando haya copiado la carpeta, el idioma aparecerá en la lista **Idioma del recurso** de la página **Tipo de aplicación** del Asistente para aplicaciones MFC.  
  
### Plantillas de idioma proporcionadas en Visual Studio .NET  
  
|Language|Plantilla|  
|--------------|---------------|  
|Chino \(Tradicional\)|1028|  
|Chino \(simplificado\)|2052|  
|Inglés|1033|  
|Francés|1036|  
|Alemán|1031|  
|Italiano|1040|  
|Japonés|1041|  
|Coreano|1042|  
|Español|3082|  
  
## Formato de archivos generados con el asistente de Visual C\+\+  
 Los asistentes de Visual C\+\+ generarán proyectos en Unicode cuando la versión de idioma instalada de Visual Studio no coincida con la configuración regional del sistema.  Por ejemplo, cuando la versión en japonés de Visual Studio está instalada en un equipo con una configuración regional en otro idioma, los asistentes de Visual C\+\+ generarán proyectos formados por archivos Unicode.  Esto suele ocurrir en equipos configurados con paquetes de interfaz de usuario multilingüe \(MUI\) de Windows.  
  
 Este comportamiento es diferente en sistemas cuya configuración regional coincide con la versión de idioma de Visual Studio.  En este caso, los archivos de proyecto se crearán en ANSI en la página de códigos del sistema.  
  
## Vea también  
 [Tipos de archivos creados para proyectos de Visual C\+\+](../ide/file-types-created-for-visual-cpp-projects.md)   
 [Creación y administración de proyectos de Visual C\+\+](../ide/creating-and-managing-visual-cpp-projects.md)