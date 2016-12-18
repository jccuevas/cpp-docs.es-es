---
title: "Especifique la ubicaci&#243;n del proyecto y los archivos de c&#243;digo fuente, Asistente para crear nuevo proyecto de archivos de c&#243;digo fuente existentes. | Microsoft Docs"
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
  - "vc.appwiz.importwiz.location"
dev_langs: 
  - "C++"
ms.assetid: 29ddffb9-5918-4d72-8c7a-a365f9de96dd
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Especifique la ubicaci&#243;n del proyecto y los archivos de c&#243;digo fuente, Asistente para crear nuevo proyecto de archivos de c&#243;digo fuente existentes.
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Utilice esta página del Asistente para crear un nuevo proyecto de archivos de código fuente existentes con el fin de especificar lo siguiente:  
  
-   La ruta de acceso del directorio del nuevo proyecto  
  
-   Los directorios donde se buscarán los archivos de código fuente existentes  
  
-   Los tipos de archivos que el asistente importará al nuevo proyecto  
  
## Lista de tareas  
 [Cómo: Crear un proyecto de C\+\+ a partir del código existente](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## Lista de UIElement  
 **Ubicación del archivo de proyecto**  
 Especifica la ruta de acceso del directorio del nuevo proyecto.  En esta ubicación el asistente depositará todos los archivos \(y subdirectorios\) del nuevo proyecto.  
  
 **Browse**  
 Abre el cuadro de diálogo **Ubicación del archivo del proyecto**, donde podrá especificar el directorio que contendrá el nuevo proyecto.  Este control permite navegar a la carpeta deseada.  
  
 **Nombre del proyecto**  
 Especifica el nombre del nuevo proyecto.  Los archivos del proyecto, con extensiones de archivo como .vcxproj, adoptarán este nombre.  Los archivos de código fuente existentes conservarán su nombre original.  
  
 **Agregar archivos al proyecto de estas carpetas**  
 Si esta opción está activada, establece el asistente para que copie al nuevo proyecto los archivos de código fuente existentes desde sus directorios originales \(que se indican en el cuadro de lista situado bajo este control\).  
  
 **Agregar subcarpetas**  
 Especifica que se copien al nuevo proyecto los archivos de código fuente de todos los subdirectorios del directorio indicado en la columna **Carpeta**.  
  
 **Carpeta**  
 Indica la ruta de acceso al directorio que contiene los archivos de código fuente existentes que se copiarán al nuevo proyecto.  Esta columna indica todos los directorios donde el asistente buscará los archivos de código fuente existentes.  
  
 **Agregar**  
 Abre el cuadro de diálogo **Agregue archivos al proyecto desde esta carpeta**, que permite especificar en qué directorios buscará el asistente los archivos de código existentes.  
  
 **Remove**  
 Elimina la ruta de acceso del directorio seleccionado en el cuadro de lista situado a la izquierda de este control.  
  
 **Tipos de archivo para agregar al proyecto**  
 Especifica los tipos de archivos que el asistente agregará al nuevo proyecto de acuerdo con las extensiones de archivo indicadas.  Las extensiones de archivo están precedidas por el carácter comodín asterisco, y separadas por signos de punto y coma en la lista.  
  
 **Mostrar todos los archivos en el Explorador de soluciones**  
 Especifica que todos los archivos del nuevo proyecto estarán visibles y aparecerán en la ventana de Explorador de soluciones.  Esta opción está habilitada de forma predeterminada.