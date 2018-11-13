---
title: 'Nuevo proyecto a partir de código existente: archivos de código fuente (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.importwiz.location
ms.assetid: 29ddffb9-5918-4d72-8c7a-a365f9de96dd
ms.openlocfilehash: e5d78b8fc6eddee7c425013c91506962853de375
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580835"
---
# <a name="specify-project-location-and-source-files-create-new-project-from-existing-code-files-wizard"></a>Especifique la ubicación del proyecto y los archivos de código fuente, Asistente para crear nuevo proyecto de archivos de código fuente existentes.

Use esta página del Asistente para crear nuevo proyecto de archivos de código fuente existentes para especificar:

- La ruta de acceso del directorio del proyecto nuevo.

- Los directorios donde buscar los archivos de código fuente existentes.

- Los tipos de archivos que el asistente importará al proyecto nuevo.

## <a name="task-list"></a>Lista de tareas

[Cómo: Crear un proyecto de C++ a partir del código existente](../ide/how-to-create-a-cpp-project-from-existing-code.md)

## <a name="uielement-list"></a>Lista de UIElement

- **Ubicación del archivo de proyecto**

   Especifica la ruta del directorio del proyecto nuevo. Esta ubicación es donde el asistente depositará todos los archivos (y subdirectorios) del proyecto nuevo.

- **Examinar**

   Muestra el cuadro de diálogo **Ubicación del archivo de proyecto**, que ayuda a especificar el directorio que contendrá el proyecto nuevo. Este control permite navegar hasta la carpeta deseada.

- **Nombre del proyecto**

   Especifica el nombre del proyecto nuevo. Los archivos de proyecto, que tienen extensiones de archivo como .vcxproj, adoptarán este nombre. Los archivos de código existentes mantendrán su nombre original.

- **Agregar archivos al proyecto desde estas carpetas**

   Cuando se activa, establece el asistente para copiar los archivos de código existentes desde sus directorios originales (que se especifican en el cuadro de lista situado debajo de este control) en el proyecto nuevo.

- **Agregar subcarpetas**

   Especifica que los archivos de código de todos los subdirectorios de la columna **Carpeta** indicada del directorio se copien en el proyecto nuevo.

- **Carpeta**

   Indica la ruta de acceso al directorio que contiene los archivos de código existentes que se van a copiar en el proyecto nuevo. En esta columna se muestran todos los directorios donde el asistente buscará los archivos de código existentes.

- **Add**

   Muestra el cuadro de diálogo **Agregar archivos al proyecto desde esta carpeta**, que ayuda a especificar los directorios donde el asistente buscará los archivos de código existentes.

- **Remove**

   Elimina la ruta de acceso del directorio que está seleccionado en el cuadro de lista situado a la izquierda de este control.

- **Tipos de archivo para agregar al proyecto**

   Especifica los tipos de archivos que el asistente agregará al proyecto nuevo en función de las extensiones de archivo especificadas. Las extensiones de archivo están precedidas por el carácter comodín de asterisco, y en la lista de extensiones de archivo se delimitan mediante un punto y coma.

- **Mostrar todos los archivos en el Explorador de soluciones**

   Especifica que todos los archivos del proyecto nuevo sean visibles y se muestren en la ventana Explorador de soluciones. Esta opción está habilitada de forma predeterminada.