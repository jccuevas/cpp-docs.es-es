---
title: Asistente para proyectos ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.atl.com.overview
helpviewer_keywords:
- ATL projects, creating
- ATL Project Wizard
ms.assetid: 564d2aaf-5b8e-4c2a-a925-ca40a283ea34
ms.openlocfilehash: 4059961d70e6486f7417a5eff034b194d9860558
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261438"
---
# <a name="atl-project-wizard"></a>Asistente para proyectos ATL

Active Template Library (ATL) es un conjunto de clases C++ basadas en plantillas que simplifican la escritura de objetos COM pequeños y rápidos. El Asistente para proyectos ATL crea un proyecto con las estructuras que contienen objetos COM.

## <a name="overview"></a>Información general

Esta página del asistente describe actual [configuración de la aplicación para el proyecto ATL](../../atl/reference/application-settings-atl-project-wizard.md) va a crear. De forma predeterminada, el proyecto tiene las siguientes opciones:

- Biblioteca de vínculos dinámicos Especifica que el servidor es un archivo DLL y, por lo tanto, un servidor en proceso.

- Especifica que el proyecto utiliza atributos con atributos.

Para cambiar estos valores predeterminados, haga clic en **configuración de la aplicación** en la columna izquierda de la Asistente y realice cambios en esa página del Asistente para proyectos ATL.

Para obtener información sobre la configuración predeterminada del proyecto, incluida la elección del juego de caracteres y la vinculación de los valores predeterminados, vea [configuraciones de proyecto ATL predeterminadas](../../atl/reference/default-atl-project-configurations.md).

Después de crear un proyecto ATL, puede agregar objetos o controles al proyecto mediante Visual C++ [asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md). Puede realizar los siguientes tipos de mejoras para un proyecto ATL básico mediante los asistentes para código:

- [Agregar objetos y controles a un proyecto ATL](../../atl/reference/adding-objects-and-controls-to-an-atl-project.md)

- [Agregar una nueva interfaz en un proyecto ATL](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)

- [Agregar un componente de COM + 1.0 a un proyecto ATL](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)

Además, tenga en cuenta estas tareas al crear y mejorar un proyecto ATL:

- [Crear un objeto ATL](../../atl/reference/making-an-atl-object-noncreatable.md)

- [Optimizar el compilador para un proyecto ATL](../../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

Puede especificar las propiedades del proyecto (por ejemplo, [si se debe vincular estáticamente a CRT](../../atl/programming-with-atl-and-c-run-time-code.md)) en el [las propiedades del proyecto](../../build/reference/general-property-page-project.md) página, puede establecer [configuraciones de compilación](/visualstudio/ide/understanding-build-configurations) para un Proyecto ATL.

## <a name="see-also"></a>Vea también

[Creación y administración de proyectos de Visual C++](../../build/creating-and-managing-visual-cpp-projects.md)<br/>
[Tipos de proyecto de Visual C++](../../build/reference/visual-cpp-project-types.md)<br/>
[Aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Programar con ATL y código en tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Tutorial](../../atl/active-template-library-atl-tutorial.md)
