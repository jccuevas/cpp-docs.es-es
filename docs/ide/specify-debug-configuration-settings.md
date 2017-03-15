---
title: "Especifique los valores de configuraci&#243;n de Debug, Asistente para crear nuevo proyecto de archivos de c&#243;digo fuente existentes. | Microsoft Docs"
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
  - "vc.appwiz.importwiz.debugsettings"
dev_langs: 
  - "C++"
ms.assetid: 607339a8-9d33-458b-8095-dc73f374e29d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Especifique los valores de configuraci&#243;n de Debug, Asistente para crear nuevo proyecto de archivos de c&#243;digo fuente existentes.
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta página del Asistente para crear nuevo proyecto de archivos de código fuente existentes se utiliza para especificar la configuración de proyecto de la versión de depuración \(Debug\).  
  
## Lista de tareas  
 [Cómo: Crear un proyecto de C\+\+ a partir del código existente](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## Lista de UIElement  
 **Línea de comandos de compilación**  
 Especifica la línea de comandos que compila el nuevo proyecto.  Por ejemplo, escriba el nombre del compilador \(y todos los modificadores o argumentos\) o los scripts de generación que desea utilizar para generar el nuevo proyecto.  Esta opción está habilitada cuando se ha seleccionado la opción **Utilizar sistema de compilación externo** en la página **Especificar configuración de proyecto**; de lo contrario, no está disponible.  
  
 **Línea de comandos de recompilación**  
 Especifica la línea de comandos que recompila el nuevo proyecto.  Esta opción está habilitada cuando se ha seleccionado la opción **Utilizar sistema de compilación externo** en la página **Especificar configuración de proyecto**; de lo contrario, no está disponible.  
  
 **Línea de comandos de limpieza**  
 Especifica la línea de comandos que se utiliza para eliminar los archivos de compatibilidad compilados por las herramientas de compilación para el nuevo proyecto.  Esta opción está habilitada cuando se ha seleccionado la opción **Utilizar sistema de compilación externo** en la página **Especificar configuración de proyecto**; de lo contrario, no está disponible.  
  
 **Resultados \(para depuración\)**  
 Especifica la ruta de acceso del directorio de los archivos de salida de la configuración de depuración del nuevo proyecto.  Esta opción está habilitada cuando se ha seleccionado la opción **Utilizar sistema de compilación externo** en la página **Especificar configuración de proyecto**; de lo contrario, no está disponible.  
  
 **Definiciones del preprocesador \(\/D\)**  
 Define los símbolos del preprocesador para el nuevo proyecto.  Para obtener más información, vea [\/D \(Definiciones de preprocesador\)](../build/reference/d-preprocessor-definitions.md).  
  
 **Incluir ruta de acceso de búsqueda \(\/I\)**  
 Especifica las rutas de acceso de los directorios que se agregarán a la lista de directorios donde el compilador buscará para resolver las referencias a archivos pasadas a las directivas del preprocesador en el nuevo proyecto.  Para obtener más información, vea [\/I \(Directorios de inclusión adicionales\)](../build/reference/i-additional-include-directories.md).  
  
 **Archivos de inclusión forzados \(\/FI\)**  
 Especifica los archivos de encabezado que se deberán procesar al compilar el nuevo proyecto.  Para obtener más información, vea [\/FI \(Dar nombre al archivo de inclusión obligatorio\)](../build/reference/fi-name-forced-include-file.md).  
  
 **Ruta de acceso de búsqueda del ensamblado .NET \(\/AI\)**  
 Especifica las rutas de acceso de los directorios donde el compilador buscará para resolver las referencias a ensamblados .NET pasadas a las directivas del preprocesador en el nuevo proyecto.  Para obtener más información, vea [\/AI \(Especificar directorios de metadatos\)](../build/reference/ai-specify-metadata-directories.md).  
  
 **Forzados usando ensamblados .NET \(\/FU\)**  
 Especifica los ensamblados .NET que se procesarán al compilar el nuevo proyecto.  Para obtener más información, vea [\/FU \(Asignar nombre al archivo \#using obligatorio\)](../build/reference/fu-name-forced-hash-using-file.md).  
  
## Vea también  
 [Especificar configuración de proyecto, Asistente para crear nuevo proyecto de archivos de código fuente existentes](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)