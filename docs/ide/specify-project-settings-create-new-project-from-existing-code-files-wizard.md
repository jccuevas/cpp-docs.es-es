---
title: Especificar configuración de proyecto, crear nuevo proyecto de Asistente para archivos de código existentes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.importwiz.appsettings
dev_langs:
- C++
helpviewer_keywords:
- Create New Project From Existing Code Files Wizard, project settings
ms.assetid: 9b8860c9-d35f-4f18-9565-2934d3d7f569
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0f59b802b5a24c1b449f78cccee4744538a5a0e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="specify-project-settings-create-new-project-from-existing-code-files-wizard"></a>Especificar configuración de proyecto, Asistente para crear nuevo proyecto de archivos de código fuente existentes
Utilice esta página del Asistente para crear nuevo proyecto de archivos de código existentes para especificar:  
  
-   El entorno de compilación para el nuevo proyecto  
  
-   La configuración para que coincida con un tipo específico de proyecto que se va a generar de compilación  
  
## <a name="task-list"></a>Lista de tareas  
 [Cómo: Crear un proyecto de C++ a partir del código existente](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Utilice Visual Studio**  
 Especifica que se use herramientas de compilación que se incluyen en Visual Studio para generar el nuevo proyecto. Esta opción está seleccionada de forma predeterminada.  
  
 **Tipo de proyecto**  
 Especifica el tipo de proyecto que generará el asistente.  
  
 **Proyecto de aplicación de Windows**  
 Indica que el asistente generará un proyecto para una aplicación ejecutable de Windows. Esta opción está disponible desde el **tipo de proyecto** cuadro de lista desplegable.  
  
 **Proyecto de aplicación de consola**  
 Indica que el asistente generará un proyecto para una aplicación de consola. Esta opción está disponible desde el **tipo de proyecto** cuadro de lista desplegable.  
  
 **Proyecto de biblioteca de vínculos dinámicos (DLL)**  
 Indica que el asistente generará un proyecto para una aplicación de biblioteca de vínculos dinámicos vacía. Esta opción está disponible desde el **tipo de proyecto** cuadro de lista desplegable.  
  
 **Proyecto de biblioteca estática (LIB)**  
 Indica que el asistente generará un proyecto para una aplicación de biblioteca estática. Esta opción está disponible desde el **tipo de proyecto** cuadro de lista desplegable.  
  
 **Agregar compatibilidad con ATL**  
 Agrega compatibilidad con ATL al nuevo proyecto.  
  
 **Agregar compatibilidad con MFC**  
 Agrega compatibilidad con MFC al nuevo proyecto.  
  
 **Agregar compatibilidad para Common Language Runtime**  
 Agrega compatibilidad para el nuevo proyecto de programación con CLR.  
  
 **Common Language Runtime**  
 Especifica el nuevo proyecto para que sea compatible con las características CLR.  
  
 **Common Language Runtime (antigua sintaxis)**  
 Especifica el nuevo proyecto para que sea compatible con las extensiones administradas para la sintaxis de C++, que son la sintaxis de programación de CLR antes de Visual C++ 2005.  
  
 **Usar el sistema de compilación externo**  
 Especifica que se use herramientas de compilación que no se incluyen en Visual Studio para generar el nuevo proyecto. Cuando se selecciona esta opción, puede especificar líneas de comandos de compilación en el **especifique los valores de configuración de Debug** y **especificar valores de configuración de Release** páginas.  
  
> [!NOTE]
>  Cuando el **sistema de compilación de uso externo** opción está activada, el IDE no genera el nuevo proyecto, por lo que el/d, / I, / Fi, /AI o /FU opciones no son necesarios para la compilación. Sin embargo, estas opciones se deben establecer correctamente en orden para que IntelliSense funcione correctamente.  
  
## <a name="see-also"></a>Vea también  
 [Especifique los valores de configuración de Debug, crear nuevo proyecto de Asistente para archivos de código existentes](../ide/specify-debug-configuration-settings.md)   
 [Especificar los valores de configuración de Release, Asistente para crear nuevo proyecto de archivos de código fuente existentes](../ide/specify-release-configuration.md)