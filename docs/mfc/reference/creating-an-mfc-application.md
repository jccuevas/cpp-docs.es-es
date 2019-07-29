---
title: Crear una aplicación MFC
ms.date: 07/28/2019
helpviewer_keywords:
- applications [MFC]
- MFC, creating applications
- MFC applications
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
ms.openlocfilehash: 454a994da6db2841317d41ea1cdacfd36b0705e4
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606473"
---
# <a name="creating-an-mfc-application"></a>Crear una aplicación MFC

Una aplicación MFC es una aplicación ejecutable para Windows basada en la biblioteca Microsoft Foundation Class (MFC). La forma más fácil de crear una aplicación MFC es usar el Asistente para aplicaciones MFC (**proyecto de aplicación MFC** en Visual Studio 2019). Para crear una aplicación de consola MFC, use el Asistente para escritorio de Windows y elija las opciones **aplicación de consola** y **encabezados de MFC** .

> [!IMPORTANT]
>  Los proyectos MFC no se admiten en las ediciones Visual Studio Express.

Los archivos ejecutables de MFC generalmente se dividen en cinco tipos: aplicaciones Windows estándar, cuadros de diálogo, aplicaciones basadas en formularios, aplicaciones de estilo Explorador y aplicaciones de estilo de explorador Web. Para más información, consulte:

- [Usar las clases para escribir aplicaciones de Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)

- [Creación y visualización de cuadros de diálogo](../../mfc/creating-and-displaying-dialog-boxes.md)

- [Creación de una aplicación MFC basada en formularios](../../mfc/reference/creating-a-forms-based-mfc-application.md)

- [Creación de una aplicación MFC estilo Explorador de archivos](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)

- [Creación de una aplicación MFC estilo explorador web](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

El Asistente para aplicaciones MFC generará las clases y los archivos apropiados para estos tipos de aplicaciones, en función de las opciones que seleccione en el asistente.

### <a name="to-create-an-mfc-application-using-the-mfc-application-wizard"></a>Para crear una aplicación MFC mediante el Asistente para aplicaciones MFC

1. Siga las instrucciones del tema de ayuda [crear un C++ proyecto de aplicación de consola](../../get-started/tutorial-console-cpp.md).

1. En el cuadro de diálogo **nuevo proyecto** , seleccione **aplicación MFC** en el panel Plantillas para abrir el asistente.

1. Defina la configuración de la aplicación mediante el [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md).

    > [!NOTE]
    >  Omita este paso para mantener la configuración predeterminada del asistente.

1. Haga clic en **Finalizar** para cerrar el asistente y abrir el proyecto nuevo en el entorno de desarrollo.

Cuando se haya creado el proyecto, podrá ver los archivos creados en el **Explorador de soluciones**. Para obtener más información sobre los archivos que crea el asistente para el proyecto, vea el archivo Readme.txt generado por el proyecto. Para más información sobre los tipos de archivo, vea [Tipos de archivo creados para proyectos de C++ de Visual Studio](../../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Vea también

[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Páginas de propiedades](../../build/reference/property-pages-visual-cpp.md)

