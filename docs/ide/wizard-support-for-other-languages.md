---
title: Compatibilidad del asistente con otros idiomas | Documentos de Microsoft
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="wizard-support-for-other-languages"></a>Compatibilidad del asistente con otros idiomas
Cuando se instala Visual Studio, la aplicación de instalación detecta la configuración regional que se muestran en el sistema e instala las plantillas para esa configuración regional o plantilla de idioma apropiado. Por ejemplo, para las configuraciones regionales europeas occidentales, el programa de instalación instala inglés, francés, italiano, español y alemán. Estos idiomas aparecen en la **idioma de recurso** lista el [tipo de aplicación](../mfc/reference/application-type-mfc-application-wizard.md) página del Asistente para aplicaciones MFC.  
  
## <a name="language-templates"></a>Plantillas de idioma  
 No todas las plantillas se instalan en todos los sistemas, ya que las plantillas son básicamente codificación ANSI, y no todos los recursos se pueden editar en todos los sistemas. Por ejemplo, de forma predeterminada, no puede editar recursos en japonés en un sistema en francés.  
  
 Si está utilizando Windows 2000 o posterior y desea crear una aplicación MFC en otro idioma, debe copiar el directorio de plantillas para el idioma adecuado desde el medio de instalador de Visual Studio (disco 1) en el sistema.  
  
> [!NOTE]
>  Para editar el proyecto creado, debe establecer la configuración regional del sistema en el idioma apropiado para el idioma seleccionado.  
  
 Las plantillas son cada uno de ellos le asigna una carpeta en el directorio \Microsoft Visual Studio .NET 2003\Vc7\VCWizards\mfcappwiz\templates\, como se muestra en la tabla siguiente. Para obtener acceso a la plantilla de idioma que desee, copie la carpeta correspondiente en el directorio \mfcappwiz\templates\ en el equipo. Una vez que haya copiado la carpeta, el idioma aparecerá en el **idioma de recurso** lista el **tipo de aplicación** página del Asistente para aplicaciones MFC.  
  
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
  
## <a name="format-of-visual-c-wizard-generated-files"></a>Formato de los archivos generados por el Asistente de C++ de Visual  
 Los asistentes de Visual C++ generarán proyectos en Unicode cuando la versión de idioma instalado de Visual Studio no coincide con la configuración regional del sistema. Por ejemplo, cuando se instala la versión en japonés de Visual Studio en un equipo que tiene la configuración regional establecida en un idioma distinto al japonés, los asistentes de Visual C++ generarán proyectos formados por archivos Unicode. Esto suele ocurrir en equipos configurados con paquetes de Windows multilingües (MUI).  
  
 Este comportamiento difiere de sistemas establecidos de forma que la configuración regional del sistema es el mismo que la versión de idioma de Visual Studio. En este caso, los archivos de proyecto se creará en ANSI en la página de códigos del sistema.  
  
## <a name="see-also"></a>Vea también  
 [Tipos de archivos creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)   
 [Creación y administración de proyectos de Visual C++](../ide/creating-and-managing-visual-cpp-projects.md)