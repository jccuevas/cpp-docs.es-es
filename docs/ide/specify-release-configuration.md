---
title: "Nuevo proyecto del código existente de la versión configuración | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.importwiz.releasesettings
dev_langs: C++
ms.assetid: 3e2fc73c-bdbd-4790-b2bd-d31731f0cece
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ff208af8bb89dbcb7df00b37ce542a5adae5fa23
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="specify-release-configuration-settings-create-new-project-from-existing-code-files-wizard"></a>Especifique los valores de configuración de Release, Asistente para crear nuevo proyecto de archivos de código fuente existentes.
Utilice esta página del Asistente Crear nuevo proyecto de archivos de código existentes para especificar la configuración de proyecto de versión.  
  
## <a name="task-list"></a>Lista de tareas  
 [Cómo: Crear un proyecto de C++ a partir del código existente](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Igual que la configuración de depuración**  
 Especifica que el asistente generará el proyecto de configuración Release idénticos para depurar la configuración de proyecto. Esta opción está activada de forma predeterminada. Todas las demás opciones de esta página están inactivas, a menos que desactive esta casilla.  
  
 **Compilar la línea de comandos**  
 Especifica la línea de comandos que genera el nuevo proyecto. Escriba el nombre del compilador además de cualquier modificadores ni argumentos que desea usar para crear el nuevo proyecto. Esta opción está habilitada cuando la **sistema de compilación utilice dicha** opción está seleccionada en el **especificar configuración de proyecto** página.  
  
 **Volver a generar la línea de comandos**  
 Especifica la línea de comandos que vuelve a generar el nuevo proyecto. Esta opción está habilitada cuando la **sistema de compilación utilice dicha** opción está seleccionada en el **especificar configuración de proyecto** página.  
  
 **Línea de comandos de limpieza**  
 Especifica la línea de comandos para eliminar archivos de compatibilidad generados por las herramientas de compilación para el nuevo proyecto. Esta opción está habilitada cuando la **sistema de compilación utilice dicha** opción está seleccionada en el **especificar configuración de proyecto** página.  
  
 **Resultados (para depuración)**  
 Especifica la ruta del directorio de los archivos de salida para la configuración de depuración del nuevo proyecto. Esta opción está habilitada cuando la **sistema de compilación utilice dicha** opción está seleccionada en el **especificar configuración de proyecto** página.  
  
 **Definiciones del preprocesador (/ d.)**  
 Define símbolos de preprocesador para el nuevo proyecto. Para obtener más información, vea [/D (Preprocessor Definitions)](../build/reference/d-preprocessor-definitions.md).  
  
 **Incluir la ruta de acceso de búsqueda (/ I)**  
 Especifica las rutas de acceso de directorio para agregar a la lista de directorios que el compilador debe buscar resolver las referencias de archivo pasado a directivas de preprocesador en el nuevo proyecto. Para obtener más información, consulte [/I (Directorios de inclusión adicionales)](../build/reference/i-additional-include-directories.md).  
  
 **Archivos de inclusión (/ FI) forzados**  
 Especifica los archivos de encabezado para procesar al generar el nuevo proyecto. Para obtener más información, consulte [/FI (Dar nombre al archivo de inclusión forzado)](../build/reference/fi-name-forced-include-file.md).  
  
 **Ruta de búsqueda del ensamblado .NET (/ AI)**  
 Especifica las rutas de acceso de directorio que el compilador debe buscar para resolver las referencias de ensamblado de .NET que se pasan a directivas de preprocesador en el nuevo proyecto. Para obtener más información, consulte [/AI (Especificar directorios de metadatos)](../build/reference/ai-specify-metadata-directories.md).  
  
 **Forzados usando ensamblados .NET (/ FU)**  
 Especifica los ensamblados de .NET para procesar al generar el nuevo proyecto. Para obtener más información, consulte [/FU (Dar nombre al archivo #using forzado)](../build/reference/fu-name-forced-hash-using-file.md).  
  
## <a name="see-also"></a>Vea también  
 [Especificar configuración de proyecto, Asistente para crear nuevo proyecto de archivos de código fuente existentes](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)