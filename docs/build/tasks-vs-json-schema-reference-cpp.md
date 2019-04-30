---
title: Referencia de esquema Tasks.vs.json (C++)
ms.date: 02/11/2019
helpviewer_keywords:
- Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: d0f62f6cddf3701da391880532bd2f554cc19130
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315058"
---
# <a name="tasksvsjson-c"></a>Tasks.vs.json (C++)

Se puede agregar un archivo `tasks.vs.json` a un proyecto Abrir carpeta para definir cualquier tarea arbitraria y luego invocarla desde el menú contextual del **Explorador de soluciones**. Normalmente los proyectos de CMake no usan este archivo porque todos los comandos de compilación se especifican en `CMakeLists.txt`. Para los sistemas de compilación diferentes de CMake, aquí es donde puede especificar los comandos de compilación e invocar los scripts de compilación. Para obtener información general sobre el uso de tasks.vs.json, vea [Personalización de las tareas de compilación y depuración para el desarrollo de "Abrir carpeta"](/visualstudio/ide/customize-build-and-debug-tasks-in-visual-studio).

