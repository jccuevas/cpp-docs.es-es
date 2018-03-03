---
title: Tipos de proyecto de Visual C++ | Documentos de Microsoft
ms.custom: 
ms.date: 10/30/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- programs [C++], projects
- project templates [Visual Studio], C++
- TODO comments [C++]
- projects [C++], types
- templates [C++], projects
- applications [C++], projects
- Visual C++ projects, types
ms.assetid: 7337987e-1e7b-4120-9a4b-94f0401f15e7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a837aa04b0e0c2b8d3d9f5cfd48181a9ea23b346
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="visual-c-project-types"></a>Tipos de proyecto de Visual C++

Se puede usar una plantilla de proyecto para crear la estructura básica de programa, menús, barras de herramientas, iconos, referencias e instrucciones `#include` adecuados para el tipo de proyecto que quiera crear. Visual Studio incluye diversos tipos de plantilla de proyecto de Visual C++, muchos de ellos con su correspondiente asistente para que pueda personalizar sus proyectos mientras los va creando. Inmediatamente después de crear un proyecto, puede generar y ejecutar la aplicación; es recomendable para compilar cada cierto tiempo mientras desarrolla la aplicación.

No es necesario usar una plantilla para crear un proyecto, pero muchas veces es lo más eficaz, dado que es más fácil modificar los archivos de proyecto y la estructura existentes que crearlos desde cero.  
  
> [!NOTE]
> Puede crear un proyecto de lenguaje C con plantillas de proyecto de C++. En el proyecto generado, busque los archivos que tengan la extensión de nombre de archivo .cpp y cámbiela por .c. Luego, en la página **Propiedades del proyecto** del proyecto (no de la solución), expanda **Propiedades de configuración**y **C/C++** y seleccione **Avanzadas**. Cambie la opción **Compilar como** por **Compilar como código de C (/TC)**.

## <a name="project-templates"></a>Plantillas de proyecto

Las plantillas de proyecto que se incluyen en Visual Studio dependen de la versión del producto y las cargas de trabajo que haya instalado. Si ha instalado el desarrollo de escritorio con cargas de trabajo de C++, Visual Studio tiene estas plantillas de proyecto de Visual C++.

### <a name="windows-desktop"></a>Escritorio de Windows

|Plantilla de proyecto|Descripción|  
|----------------------|-----------------------------| 
|[Aplicación de consola de Windows](../windows/creating-a-console-application.md)|Un proyecto para crear una aplicación de consola de Windows.|
|[Aplicación de escritorio de Windows](../windows/walkthrough-creating-windows-desktop-applications-cpp.md)|Proyecto para crear una aplicación de escritorio (Win32) de Windows.|
|[Biblioteca de vínculos dinámicos](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)|Un proyecto para crear una biblioteca de vínculos dinámicos (DLL).|
|[Biblioteca estática](../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|Un proyecto para crear una biblioteca estática (LIB).|
|Asistente para escritorio de Windows|Un Asistente para crear bibliotecas y aplicaciones de escritorio de Windows con opciones adicionales.|

### <a name="general"></a>General

|Plantilla de proyecto|Descripción|
|----------------------|-----------------------------|
|Proyecto vacío|Un proyecto vacío para crear una aplicación, la biblioteca o el archivo DLL. Debe agregar cualquier código o los recursos necesarios.|
|[Proyecto de archivos MAKE](../ide/creating-a-makefile-project.md)|Sistema de compilación de un proyecto para usarlo con una referencia externa.|
|Compartir proyecto elementos|Un proyecto que se utiliza para compartir archivos entre varios proyectos.|

### <a name="atl"></a>ATL

|Plantilla de proyecto|Descripción|
|----------------------|-----------------------------|
|[Proyecto ATL](../atl/reference/creating-an-atl-project.md)|Un proyecto que usa Active Template Library.|

### <a name="test"></a>Prueba

|Plantilla de proyecto|Descripción|
|----------------------|-----------------------------|
|[Proyecto de prueba unitaria nativo](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)|Un proyecto que contiene pruebas unitarias de C++ nativo.|

### <a name="mfc"></a>MFC

Si agrega que la MFC y ATL admiten componente a la instalación de Visual Studio, se agregan estas plantillas de proyecto en Visual Studio.

|Plantilla de proyecto|Descripción|
|----------------------|-----------------------------|
|[Aplicación MFC](../mfc/reference/creating-an-mfc-application.md)|Proyecto para crear una aplicación que utiliza la biblioteca (Microsoft Foundation Classes).|
|[Control ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md)|Un proyecto para crear un control ActiveX que utiliza la biblioteca MFC.|
|[ARCHIVOS DLL DE MFC](../mfc/reference/creating-an-mfc-dll-project.md)|Un proyecto para crear una biblioteca de vínculos dinámicos que usa la biblioteca MFC.|

### <a name="windows-universal-apps"></a>Aplicaciones universales de Windows

Si agrega el componente de herramientas de plataforma Universal de Windows de C++ a la instalación de Visual Studio, se agregan estas plantillas de proyecto en Visual Studio.

Para obtener información general de las aplicaciones universales de Windows en C++, vea [aplicaciones universales de Windows (C++)](../windows/universal-windows-apps-cpp.md).

|Plantilla de proyecto|Descripción|
|----------------------|-----------------------------|
|Aplicación vacía|Un proyecto para una aplicación de plataforma Universal de Windows (UWP) de una página que no tenga diseño o controles predefinidos.|
|Aplicación de DirectX 11|Un proyecto para una aplicación de plataforma Universal de Windows que utiliza DirectX 11.|
|Aplicación DirectX 12|Un proyecto para una aplicación de plataforma Universal de Windows que utiliza DirectX 12.|
|DirectX 11 y aplicación XAML|Un proyecto para una aplicación de plataforma Universal de Windows que utiliza DirectX 11 y XAML.|
|Aplicación de prueba unitaria|Un proyecto para crear una aplicación de prueba unitaria para las aplicaciones de la plataforma Universal de Windows (UWP).|
|Archivo DLL|Un proyecto para una biblioteca de vínculos dinámicos (DLL) nativa que se puede usar un componente de aplicación o en tiempo de ejecución de la plataforma Universal de Windows.|
|Biblioteca estática|Un proyecto para una biblioteca de vínculos estáticos nativa (LIB) que se puede usar un componente de aplicación o en tiempo de ejecución de la plataforma Universal de Windows.|
|Componente de Windows Runtime|Un proyecto para un componente en tiempo de ejecución de Windows que puede usarse en una aplicación de plataforma Universal de Windows, independientemente del lenguaje de programación en el que se escribe la aplicación.|
|Proyecto de empaquetado de aplicaciones de Windows|Un proyecto que crea un paquete UWP que permite que una aplicación de escritorio para carga lateral o distribuidas a través de Microsoft Store.|

## <a name="todo-comments"></a>Comentarios TODO

Muchos de los archivos que se generan mediante una plantilla de proyecto contienen comentarios TODO que ayudan a saber dónde puede incluir su propio código fuente. Para obtener más información sobre cómo agregar código, consulte [agregar funcionalidad con los asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md) y [trabajar con archivos de recursos](../windows/working-with-resource-files.md).

## <a name="see-also"></a>Vea también

[Crear proyectos de escritorio con asistentes para aplicaciones](../ide/creating-desktop-projects-by-using-application-wizards.md)   
