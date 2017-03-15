---
title: "Especificar configuraci&#243;n de proyecto, Asistente para crear nuevo proyecto de archivos de c&#243;digo fuente existentes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.importwiz.appsettings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para crear nuevo proyecto de archivos de código fuente existentes, configuración de proyecto"
ms.assetid: 9b8860c9-d35f-4f18-9565-2934d3d7f569
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# Especificar configuraci&#243;n de proyecto, Asistente para crear nuevo proyecto de archivos de c&#243;digo fuente existentes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Utilice esta página del Asistente para crear un nuevo proyecto de archivos de código fuente existentes con el fin de especificar lo siguiente:  
  
-   El entorno de compilación del nuevo proyecto  
  
-   La configuración de compilación que deberá coincidir con un determinado tipo de proyecto nuevo que se desea compilar  
  
## Lista de tareas  
 [Cómo: Crear un proyecto de C\+\+ a partir del código existente](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## Lista de UIElement  
 **Utilizar Visual Studio**  
 Especifica que se desea utilizar las herramientas de compilación incluidas en Visual Studio para compilar el nuevo proyecto.  Esta opción está seleccionada de forma predeterminada.  
  
 **Tipo de proyecto**  
 Especifica el tipo de proyecto que generará el asistente.  
  
 **Proyecto de aplicación para Windows**  
 Indica que el asistente generará un proyecto para una aplicación para Windows ejecutable.  Esta opción está disponible en el cuadro de lista desplegable **Tipo de proyecto**.  
  
 **Proyecto de aplicación de consola**  
 Indica que el asistente generará un proyecto para una aplicación de consola.  Esta opción está disponible en el cuadro de lista desplegable **Tipo de proyecto**.  
  
 **Proyecto de biblioteca de vínculos dinámicos \(DLL\)**  
 Indica que el asistente generará un proyecto para una aplicación de biblioteca de vínculos dinámicos vacía.  Esta opción está disponible en el cuadro de lista desplegable **Tipo de proyecto**.  
  
 **Proyecto de biblioteca estática \(LIB\)**  
 Indica que el asistente generará un proyecto para una aplicación de biblioteca estática.  Esta opción está disponible en el cuadro de lista desplegable **Tipo de proyecto**.  
  
 **Agregar compatibilidad para ATL**  
 Agrega compatibilidad con ATL al nuevo proyecto.  
  
 **Agregar compatibilidad para MFC**  
 Agrega compatibilidad con MFC al nuevo proyecto.  
  
 **Agregar compatibilidad para Common Language Runtime**  
 Agrega compatibilidad de programación con CLR al nuevo proyecto.  
  
 **Common Language Runtime**  
 Especifica que el nuevo proyecto sea compatible con características CLR.  
  
 **Common Language Runtime \(sintaxis antigua\)**  
 Especifica que el nuevo proyecto sea conforme a la sintaxis de Extensiones administradas para C\+\+, que es la sintaxis de programación CLR anterior a Visual C\+\+ 2005.  
  
 **Utilizar sistema de compilación externo**  
 Especifica que se desea utilizar las herramientas de compilación no incluidas en Visual Studio para compilar el nuevo proyecto.  Cuando se selecciona esta opción, es posible especificar las líneas de comandos de compilación en las páginas **Especifique los valores de configuración de Debug** y **Especifique los valores de configuración de lanzamiento**.  
  
> [!NOTE]
>  Cuando se selecciona la opción **Utilizar sistema de generación externo**, el IDE no genera el nuevo proyecto, de modo que las opciones \/D, \/I, \/FI, \/AI o \/FU no son necesarias para la compilación.  Sin embargo, estas opciones se deben establecer correctamente para que IntelliSense funcione adecuadamente.  
  
## Vea también  
 [Especifique los valores de configuración de Debug, Asistente para crear nuevo proyecto de archivos de código fuente existentes.](../ide/specify-debug-configuration-settings.md)   
 [Especifique los valores de configuración de Release, Asistente para crear nuevo proyecto de archivos de código fuente existentes.](../ide/specify-release-configuration.md)