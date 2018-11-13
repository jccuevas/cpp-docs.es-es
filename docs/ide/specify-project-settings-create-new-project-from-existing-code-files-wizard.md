---
title: Especificar configuración de proyecto, Asistente para crear nuevo proyecto de archivos de código fuente existentes
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.importwiz.appsettings
helpviewer_keywords:
- Create New Project From Existing Code Files Wizard, project settings
ms.assetid: 9b8860c9-d35f-4f18-9565-2934d3d7f569
ms.openlocfilehash: f46436295e16d527718e59f1c4c199643f9e35ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522348"
---
# <a name="specify-project-settings-create-new-project-from-existing-code-files-wizard"></a>Especificar configuración de proyecto, Asistente para crear nuevo proyecto de archivos de código fuente existentes

Use esta página del Asistente para crear nuevo proyecto de archivos de código fuente existentes para especificar:

- El entorno de compilación para el proyecto.

- La configuración de compilación para que coincida con un tipo específico de proyecto nuevo que se va a generar.

## <a name="task-list"></a>Lista de tareas

[Cómo: Crear un proyecto de C++ a partir del código existente](../ide/how-to-create-a-cpp-project-from-existing-code.md)

## <a name="uielement-list"></a>Lista de UIElement

- **Usar Visual Studio**

   Especifica que se usen las herramientas de compilación que se incluyen en Visual Studio para generar el proyecto nuevo. Esta opción está seleccionada de forma predeterminada.

- **Tipo de proyecto**

   Especifica el tipo de proyecto que va a generar el asistente.

- **Proyecto de aplicación Windows**

   Indica que el asistente va a generar un proyecto para una aplicación Windows ejecutable. Esta opción está disponible desde el cuadro de lista desplegable **Tipo de proyecto**.

- **Proyecto de aplicación de consola**

   Indica que el asistente va a generar un proyecto para una aplicación de consola. Esta opción está disponible desde el cuadro de lista desplegable **Tipo de proyecto**.

- **Proyecto de biblioteca de vínculos dinámicos (DLL)**

   Indica que el asistente va a generar un proyecto para una aplicación de biblioteca de vínculos dinámicos vacía. Esta opción está disponible desde el cuadro de lista desplegable **Tipo de proyecto**.

- **Proyecto de biblioteca estática (LIB)**

   Indica que el asistente va a generar un proyecto para una aplicación de biblioteca estática. Esta opción está disponible desde el cuadro de lista desplegable **Tipo de proyecto**.

- **Agregar compatibilidad con ATL**

   Agrega compatibilidad con ATL al proyecto nuevo.

- **Agregar compatibilidad con MFC**

   Agrega compatibilidad con MFC al proyecto nuevo.

- **Agregar compatibilidad con Common Language Runtime**

   Agrega compatibilidad con la programación de CLR al proyecto nuevo.

- **Common Language Runtime**

   Especifica el proyecto nuevo para que sea compatible con las características de CLR.

- **Common Language Runtime (sintaxis anterior)**

   Especifica el proyecto nuevo para que sea compatible con la sintaxis de Extensiones administradas para C++, que es la sintaxis de programación de CLR anterior a Visual C++ 2005.

- **Usar el sistema de compilación externo**

   Especifica que se usen las herramientas de compilación que no se incluyen en Visual Studio para generar el proyecto nuevo. Cuando esta opción está seleccionada, puede especificar líneas de comandos de compilación en las páginas **Especificar valores de configuración Debug** y **Especificar valores de configuración Release**.

   > [!NOTE]
   > Cuando se activa la opción **Usar el sistema de compilación externo**, el IDE no genera el proyecto nuevo, por lo que no se necesitan las opciones /D, /I, /FI, /AI o /FU para la compilación. Pero estas opciones se deben establecer de manera correcta para que IntelliSense funcione correctamente.

## <a name="see-also"></a>Vea también

[Especificar los valores de configuración de Debug, Asistente para crear nuevo proyecto de archivos de código fuente existentes](../ide/specify-debug-configuration-settings.md)<br>
[Especificar los valores de configuración de Release, Asistente para crear nuevo proyecto de archivos de código fuente existentes](../ide/specify-release-configuration.md)