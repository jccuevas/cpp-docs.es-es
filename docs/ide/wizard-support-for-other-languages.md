---
title: Compatibilidad del asistente con otros idiomas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.EastAsianLanguages
dev_langs:
- C++
helpviewer_keywords:
- wizards [C++], language support
- language support for MFC projects
- projects [C++], language support
ms.assetid: b653c673-0687-455c-885f-15d7e2f4149d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75aafd7177c3799c17b75419fd5ab9f54af91d35
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332447"
---
# <a name="wizard-support-for-other-languages"></a>Compatibilidad del asistente con otros idiomas
Cuando se instala Visual Studio, la aplicación de instalación detecta la configuración regional que se muestra en el sistema e instala las plantillas de idioma apropiadas para esa configuración regional. Por ejemplo, para las configuraciones regionales de Europa Occidental, el programa de instalación instala inglés, francés, italiano, español y alemán. Estos idiomas aparecen en la lista **Idioma de recurso** en la página [Tipo de aplicación](../mfc/reference/application-type-mfc-application-wizard.md) del Asistente para aplicaciones MFC.  
  
## <a name="language-templates"></a>Plantillas de idioma  
 No todas las plantillas se instalan en todos los sistemas, ya que las plantillas se basan en codificación ANSI, y no todos los recursos se pueden editar en todos los sistemas. Por ejemplo, de forma predeterminada, no se pueden editar los recursos en japonés en un sistema en francés.  
  
 Si usa Windows 2000 o una versión posterior y quiere crear una aplicación MFC en otro idioma, debe copiar el directorio de plantillas para el idioma adecuado desde el medio del instalador de Visual Studio (Disco 1) al sistema.  
  
> [!NOTE]
>  Para editar el proyecto creado, debe establecer la configuración regional del sistema en la configuración regional apropiada para el idioma seleccionado.  
  
 A cada plantilla se le asigna una carpeta en el directorio \Microsoft Visual Studio .NET 2003\Vc7\VCWizards\mfcappwiz\templates\, como se muestra en la tabla siguiente. Para acceder a la plantilla de idioma deseada, copie la carpeta correspondiente en el directorio \mfcappwiz\templates\ en el equipo. Después de copiar la carpeta, el idioma aparecerá en la lista **Idioma de recurso** en la página **Tipo de aplicación** del Asistente para aplicaciones MFC.  
  
### <a name="language-templates-provided-in-visual-studio-net"></a>Plantillas de idioma proporcionadas en Visual Studio .NET  
  
|Lenguaje|Plantilla|  
|--------------|--------------|  
|Chino (tradicional)|1028|  
|Chino (simplificado)|2052|  
|Inglés|3082|  
|Francés|1036|  
|Alemán|1031|  
|Italiano|1040|  
|Japonés|1041|  
|Coreano|1042|  
|Español|3082|  
  
## <a name="format-of-visual-c-wizard-generated-files"></a>Formato de los archivos generados por el Asistente de Visual C++  
 Los asistentes de Visual C++ generarán proyectos en Unicode cuando la versión de idioma instalada de Visual Studio no coincida con la configuración regional del sistema. Por ejemplo, cuando se instala la versión en japonés de Visual Studio en un equipo que tiene la configuración regional establecida en un idioma distinto al japonés, los asistentes de Visual C++ generarán proyectos formados por archivos Unicode. Esto suele ocurrir en los equipos configurados con paquetes multilingües (MUI) de Windows.  
  
 Este comportamiento difiere de los sistemas establecidos de forma que la configuración regional del sistema es la misma que la versión de idioma de Visual Studio. En este caso, los archivos de proyecto se crearán en ANSI en la página de códigos del sistema.  
  
## <a name="see-also"></a>Vea también  
 [Tipos de archivos creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)   
 [Creación y administración de proyectos de Visual C++](../ide/creating-and-managing-visual-cpp-projects.md)