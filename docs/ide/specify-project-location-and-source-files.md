---
title: "Nuevo proyecto del código existente - archivos de código fuente (Visual C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.importwiz.location
dev_langs: C++
ms.assetid: 29ddffb9-5918-4d72-8c7a-a365f9de96dd
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 36b20340da6cae933acb0650b3e073e3835a0204
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="specify-project-location-and-source-files-create-new-project-from-existing-code-files-wizard"></a>Especifique la ubicación del proyecto y los archivos de código fuente, Asistente para crear nuevo proyecto de archivos de código fuente existentes.
Utilice esta página del Asistente para crear nuevo proyecto de archivos de código existentes para especificar:  
  
-   La ruta del directorio del nuevo proyecto  
  
-   Los directorios donde buscar archivos de código fuente existentes  
  
-   Los tipos de archivos que el asistente importará al nuevo proyecto  
  
## <a name="task-list"></a>Lista de tareas  
 [Cómo: Crear un proyecto de C++ a partir del código existente](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Ubicación del archivo de proyecto**  
 Especifica la ruta del directorio del nuevo proyecto. Esta ubicación es donde deposite el Asistente para todos los archivos (y subdirectorios) del nuevo proyecto.  
  
 **Examinar**  
 Muestra el **ubicación del archivo de proyecto** cuadro de diálogo, que le ayuda a especificar el directorio que contendrá el nuevo proyecto. Este control permite navegar hasta la carpeta deseada.  
  
 **Nombre del proyecto**  
 Especifica el nombre del nuevo proyecto. Archivos de proyecto, que tienen extensiones de archivo como .vcxproj adoptarán este nombre. Archivos de código existentes mantendrá su nombre original.  
  
 **Agregar archivos al proyecto de estas carpetas**  
 Cuando se activa, Establece el Asistente para copiar archivos de código existentes desde sus directorios originales (que se especifican en el cuadro de lista situado bajo este control) en el nuevo proyecto.  
  
 **Agregar subcarpetas**  
 Especifica copiar archivos de código de todos los subdirectorios del directorio de la lista **carpeta** columna al nuevo proyecto.  
  
 **Carpeta**  
 Indica la ruta de acceso al directorio que contiene los archivos de código existentes que se copia en el nuevo proyecto. Esta columna muestra todos los directorios que el asistente buscará archivos de código existentes.  
  
 **Add**  
 Muestra el **agregar archivos al proyecto desde esta carpeta** cuadro de diálogo que le ayuda a especificar directorios que el asistente buscará archivos de código existentes.  
  
 **Remove**  
 Elimina la ruta del directorio que está seleccionada en la izquierda del cuadro de lista de este control.  
  
 **Tipos de archivo para agregar al proyecto**  
 Especifica los tipos de archivos que el asistente agregará al nuevo proyecto basado en las extensiones de archivo especificado. Extensiones de archivo están precedidas por el carácter comodín de asterisco y en la lista de extensiones de archivo se delimitan por un punto y coma.  
  
 **Mostrar todos los archivos en el Explorador de soluciones**  
 Especifica que todos los archivos en el nuevo proyecto sea visible y se muestran en la ventana Explorador de soluciones. Esta opción está habilitada de forma predeterminada.