---
title: "Archivos creados para un asistente | Microsoft Docs"
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
  - "asistentes personalizados, eliminar archivos"
  - "asistentes personalizados, archivos creados"
  - "archivos [C++], creado mediante un asistente personalizado"
  - "iconos, eliminar"
ms.assetid: 7f0e393c-395e-491b-add2-904cf8838e81
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Archivos creados para un asistente
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El asistente utiliza el nombre especificado en el cuadro **Nombre** del cuadro de diálogo **Nuevo proyecto** para derivar los nombres de algunos archivos y clases.  
  
 El [Asistente personalizado](../ide/custom-wizard.md) agrega comentarios a los archivos que crea para el asistente.  Además, crea un archivo de texto \(readme.txt\) en el directorio de la nueva aplicación.  En este archivo se explica el contenido y el uso del resto de los archivos creados por el Asistente personalizado.  
  
 En la siguiente tabla se describen los archivos creados por el Asistente personalizado.  Si desea obtener más información sobre la interacción de los elementos clave en la creación de un asistente, vea [Diseñar un asistente](../ide/designing-a-wizard.md).  
  
|Archivo|Descripción|  
|-------------|-----------------|  
|[Project.vsz](../ide/dot-vsz-file-project-control.md)|Archivo de texto que es similar al antiguo formato .ini.  Identifica el motor del asistente y proporciona contexto y [parámetros personalizados](../ide/custom-parameters-in-the-wizard-dot-vsz-file.md) opcionales.|  
|[Project.vsdir](../Topic/Adding%20Wizards%20to%20the%20Add%20Item%20and%20New%20Project%20Dialog%20Boxes%20by%20Using%20.Vsdir%20Files.md)|Archivo de texto que permite al shell de Visual Studio encontrar el asistente y mostrarlo en el cuadro de diálogo **Nuevo proyecto**.|  
|[Archivos HTML \(opcional\)](../ide/html-files.md)|Los asistentes pueden contener interfaces de usuario de tipo HTML.  Los asistentes sin interfaz de usuario no contienen archivos HTML.<br /><br /> Si un asistente tiene una interfaz de usuario, cada pantalla individual del asistente se denomina *página* y en cada página se especifican características de la interfaz de usuario.<br /><br /> El archivo default.htm define la primera página del asistente.  Use el cuadro de lista **Número de páginas** de [Configuración de la aplicación, Asistente personalizado](../ide/application-settings-custom-wizard.md) para especificar las páginas adicionales.  Cada página adicional viene definida por un archivo Page\_*númeroDePágina*.htm, donde *númeroDePágina* especifica un número comprendido entre 2 y el número de páginas que se especifique.|  
|[Archivos de script](../ide/jscript-file.md)|El Asistente personalizado crea un archivo JScript, default.js, para cada asistente que se crea.  Este archivo contiene funciones de JScript que obtienen acceso al Asistente para Visual C\+\+, así como a los modelos de código y de objetos del entorno de Visual C\+\+ para personalizar los asistentes.  Es posible personalizar el archivo default.js del asistente y agregarle funciones.<br /><br /> Además, el asistente incluye el archivo [common.js](../ide/customizing-cpp-wizards-with-common-jscript-functions.md), que contiene funciones de uso común de JScript; este archivo lo comparten todos los asistentes, incluidos los asistentes utilizados por Visual Studio C\+\+ para crear otros tipos de proyectos.  Para obtener más información, vea [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md).|  
|[Plantillas](../ide/template-files.md)|Las plantillas de un asistente son un conjunto de archivos de texto que contienen directivas que se analizan e insertan en la tabla de símbolos en función de las selecciones efectuadas por el usuario en el asistente.  Los archivos de texto de las plantillas se representan según los datos proporcionados por el usuario y, después, se agregan al proyecto creado por el asistente.  La información apropiada se obtiene directamente de la tabla de símbolos del control del asistente.|  
|[Templates.inf](../ide/templates-inf-file.md)|Archivo de texto que detalla todas las plantillas asociadas al proyecto.|  
|Default.vcxproj|Archivo .xml que contiene la información del tipo de proyecto.|  
|Sample.txt|Archivo de plantilla que muestra cómo se utilizan las directivas del asistente.|  
|ReadMe.txt|Archivo de plantilla que contiene un resumen de cada uno de los archivos creados por el Asistente personalizado.|  
|Imágenes \(opcional\)|Se puede suministrar cualquier tipo de imágenes \(como iconos, GIF, BMP y otros formatos de imagen compatibles con HTML\) para mejorar la interfaz de usuario del asistente.  Los asistentes sin interfaz de usuario no requieren imágenes.|  
|Styles.css \(opcional\)|Archivo que define los estilos de la interfaz de usuario.  Si el asistente no tiene interfaz de usuario, el Asistente personalizado no creará un archivo .css.|  
  
 Si se eliminan los archivos y directorios del asistente, también deberán eliminarse los siguientes archivos del directorio \\vc7\\vcprojects\\.  Hasta que elimine estos archivos, los iconos del asistente seguirán apareciendo en el cuadro de diálogo **Nuevo proyecto**.  
  
-   *nombredeproyecto*.vsz  
  
-   *nombredeproyecto*.ico  
  
-   *nombredeproyecto*.vsdir  
  
## Vea también  
 [asistente personalizado](../ide/custom-wizard.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)