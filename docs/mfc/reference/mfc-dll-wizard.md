---
title: Asistente para archivos DLL de MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.dll.overview
helpviewer_keywords:
- MFC DLLs [MFC], creating
- MFC DLL Wizard
- DLLs [MFC], MFC
- DLL wizard [MFC]
- MFC DLLs [MFC]
- DLLs [MFC], creating
ms.assetid: 4e936031-7e39-4f40-a295-42a09c5ff264
ms.openlocfilehash: c0c8edfd26fc6abdcef1cbb2cfa93d88f9a37cde
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822709"
---
# <a name="mfc-dll-wizard"></a>Asistente para archivos DLL de MFC

Cuando usa el Asistente para la DLL de MFC para crear un proyecto DLL de MFC, obtendrá una aplicación inicial que funciona con funcionalidad integrada que, al compilar, implementará las características básicas de un [DLL](../../build/dlls-in-visual-cpp.md). El programa MFC inicial incluye archivos de código fuente (.cpp) de C++, los archivos de recursos (.rc) y un archivo de proyecto (.vcxproj). El código generado en estos archivos iniciales se basa en MFC. Para obtener más información, consulte los detalles del archivo en el archivo Readme.txt que se genera para el proyecto en Visual Studio, y [clases y funciones generadas por el Asistente para archivos DLL de MFC](../../mfc/reference/classes-and-functions-generated-by-the-mfc-dll-wizard.md)

## <a name="overview"></a>Información general

Esta página del asistente describe actual [configuración de la aplicación para el proyecto DLL de MFC](../../mfc/reference/application-settings-mfc-dll-wizard.md) va a crear. De forma predeterminada, se crea el proyecto como un proyecto de DLL de MFC (MFC compartido) normal sin ninguna configuración adicional.

Para cambiar estos valores predeterminados, haga clic en **configuración de la aplicación** en la columna izquierda de la Asistente y realice cambios en esa página del Asistente para la DLL de MFC.

Después de crear un proyecto DLL de MFC, puede agregar objetos o controles al proyecto mediante Visual C++ [asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md).

Puede realizar las tareas y los tipos de mejoras para un proyecto de DLL de MFC básico siguientes:

- [Exportar desde un archivo DLL](../../build/exporting-from-a-dll.md)

- [Vincular un ejecutable a un archivo DLL](../../build/linking-an-executable-to-a-dll.md)

- [Inicializar un archivo DLL](../../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="see-also"></a>Vea también

[Creación y administración de proyectos de Visual C++](../../build/creating-and-managing-visual-cpp-projects.md)<br/>
[Páginas de propiedades](../../build/reference/property-pages-visual-cpp.md)<br/>
[Conjunto de compilador y las propiedades de compilación](../../build/working-with-project-properties.md)<br/>
[Clase MFC](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Implementar una interfaz](../../ide/implementing-an-interface-visual-cpp.md)<br/>
