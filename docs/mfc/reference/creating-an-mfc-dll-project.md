---
title: Crear un proyecto DLL de MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfcdll.project
helpviewer_keywords:
- MFC DLLs [MFC], creating projects
- DLLs [MFC], MFC
- projects [MFC], creating
- DLLs [MFC], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
ms.openlocfilehash: 21173582f68b1d50fefbe22250546fcce63730b4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278839"
---
# <a name="creating-an-mfc-dll-project"></a>Crear un proyecto DLL de MFC

Un archivo DLL de MFC es un archivo binario que actúa como una biblioteca compartida de funciones que pueden utilizar simultáneamente varias aplicaciones. La forma más fácil de crear un proyecto DLL de MFC es utilizar el Asistente para archivos DLL de MFC.

> [!NOTE]
>  Las características del IDE pueden depender de la edición o configuración activa, y ser diferentes de las que se describen en la Ayuda. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>Para crear un proyecto DLL de MFC mediante el Asistente para archivos DLL de MFC

1. Siga las instrucciones descritas en el tema de Ayuda [Crear un proyecto con el Asistente para aplicaciones de Visual C++](../../ide/creating-desktop-projects-by-using-application-wizards.md).

**Tenga en cuenta** en el **nuevo proyecto** cuadro de diálogo, seleccione el `MFC DLL` icono en el panel Plantillas para abrir el Asistente para archivos DLL de MFC.

1. Defina la configuración de aplicación mediante el [configuración de la aplicación](../../mfc/reference/application-settings-mfc-dll-wizard.md) página de la [Asistente para archivos DLL de MFC](../../mfc/reference/mfc-dll-wizard.md).

    > [!NOTE]
    >  Omita este paso para mantener la configuración predeterminada del asistente.

1. Haga clic en **finalizar** para cerrar el asistente y abrir el proyecto nuevo en **el Explorador de soluciones**.

Una vez creado el proyecto, puede ver los archivos creados en **el Explorador de soluciones**. Para obtener más información sobre los archivos que crea el asistente para el proyecto, vea el archivo Readme.txt generado por el proyecto. Para obtener más información acerca de los tipos de archivo, consulte [tipos de archivo creados para proyectos de Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Vea también

[Tipos de proyecto de Visual C++](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Páginas de propiedades](../../ide/property-pages-visual-cpp.md)
