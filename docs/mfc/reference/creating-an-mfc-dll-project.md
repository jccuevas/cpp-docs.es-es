---
title: Crear un proyecto DLL de MFC
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.mfcdll.project
helpviewer_keywords:
- MFC DLLs [MFC], creating projects
- DLLs [MFC], MFC
- projects [MFC], creating
- DLLs [MFC], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
ms.openlocfilehash: 6367b2a4b85b2c586c5a4420a8be1f80d334b2e4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363958"
---
# <a name="creating-an-mfc-dll-project"></a>Crear un proyecto DLL de MFC

Un archivo DLL de MFC es un archivo binario que actúa como una biblioteca compartida de funciones que pueden utilizar simultáneamente varias aplicaciones. La forma más fácil de crear un proyecto DLL de MFC es utilizar el Asistente para archivos DLL de MFC.

> [!NOTE]
> Las características del IDE pueden depender de la edición o configuración activa, y ser diferentes de las que se describen en la Ayuda. Para cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>Para crear un proyecto DLL de MFC mediante el Asistente para archivos DLL de MFC

1. Siga las instrucciones del tema de ayuda Creación de [una aplicación MFC,](creating-an-mfc-application.md) pero elija Biblioteca de **vínculos dinámicos MFC** o DLL de **MFC** en la lista de plantillas disponibles.

1. Defina la configuración de la aplicación mediante la página de configuración de la [aplicación](../../mfc/reference/application-settings-mfc-dll-wizard.md) del Asistente para DLL de [MFC.](../../mfc/reference/mfc-dll-wizard.md)

    > [!NOTE]
    >  Omita este paso para mantener la configuración predeterminada del asistente.

1. Haga clic en **Finalizar** para cerrar el asistente y abrir el nuevo proyecto en el Explorador de **soluciones**.

Cuando se haya creado el proyecto, podrá ver los archivos creados en el **Explorador de soluciones**. Para obtener más información sobre los archivos que crea el asistente para el proyecto, vea el archivo Readme.txt generado por el proyecto. Para más información sobre los tipos de archivo, vea [Tipos de archivo creados para proyectos de C++ de Visual Studio](../../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Consulte también

[Tipos de proyectos de C++ en Visual Studio](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Páginas de propiedades](../../build/reference/property-pages-visual-cpp.md)
