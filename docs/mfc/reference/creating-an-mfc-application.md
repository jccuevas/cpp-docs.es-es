---
title: Crear una aplicación MFC
ms.date: 08/28/2019
helpviewer_keywords:
- applications [MFC]
- MFC, creating applications
- MFC applications
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
ms.openlocfilehash: 5f3a24a46db1c9013e5458143812faa079ade013
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108500"
---
# <a name="creating-an-mfc-application"></a>Crear una aplicación MFC

Una aplicación MFC es una aplicación ejecutable para Windows basada en la biblioteca Microsoft Foundation Class (MFC). Los archivos ejecutables de MFC generalmente se dividen en cinco tipos: aplicaciones Windows estándar, cuadros de diálogo, aplicaciones basadas en formularios, aplicaciones de estilo Explorador y aplicaciones de estilo de explorador Web. Para más información, consulte:

- [Usar las clases para escribir aplicaciones de Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)

- [Creación y visualización de cuadros de diálogo](../../mfc/creating-and-displaying-dialog-boxes.md)

- [Creación de una aplicación MFC basada en formularios](../../mfc/reference/creating-a-forms-based-mfc-application.md)

- [Creación de una aplicación MFC estilo Explorador de archivos](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)

- [Creación de una aplicación MFC estilo explorador web](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

El Asistente para aplicaciones MFC generará las clases y los archivos apropiados para estos tipos de aplicaciones, en función de las opciones que seleccione en el asistente.


La forma más fácil de crear una aplicación MFC es usar el Asistente para aplicaciones MFC (**proyecto de aplicación MFC** en Visual Studio 2019). Para crear una aplicación de consola MFC (un programa de línea de comandos que usa las bibliotecas MFC pero se ejecuta en la ventana de la consola), use el Asistente para escritorio de Windows y elija las opciones **aplicación de consola** y **encabezados de MFC** .

::: moniker range=">=vs-2019"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>Para crear una aplicación basada en cuadros de diálogo o formularios MFC

1. En el menú principal, elija **archivo** > **nuevo** > **proyecto**.
1. Escriba "MFC" en el cuadro de búsqueda y, a continuación, elija **aplicación MFC** en la lista de resultados.
1. Modifique los valores predeterminados según sea necesario y, después, haga clic en **crear** para abrir el **Asistente para aplicaciones MFC**.
1. Modifique los valores de configuración según sea necesario y, después, presione **Finalizar**.

Para obtener más información, vea [crear una aplicación MFC basada en formularios](creating-a-forms-based-mfc-application.md).

![Asistente para aplicaciones MFC](media/mfc-app-wizard.png)

## <a name="to-create-an-mfc-console-application"></a>Para crear una aplicación de consola MFC

Una aplicación de consola MFC es un programa de línea de comandos que usa las bibliotecas MFC, pero se ejecuta en la ventana de la consola.

1. En el menú principal, elija **archivo** > **nuevo** > **proyecto**.
1. Escriba "escritorio" en el cuadro de búsqueda y, a continuación, elija **Asistente para escritorio de Windows** en la lista de resultados.
1. Modifique el nombre del proyecto según sea necesario y, a continuación, presione **siguiente** para abrir el **Asistente para escritorio de Windows**.
1. Active la casilla **encabezados de MFC** y establezca otros valores según sea necesario y, a continuación, presione **Finalizar**.

![Asistente para aplicaciones MFC](media/windows-desktop-wizard.png)

::: moniker-end

::: moniker range="=vs-2017"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>Para crear una aplicación basada en cuadros de diálogo o formularios MFC

1. En el menú principal, elija **archivo** > **nuevo** > **proyecto**.
1. En las plantillas instaladas, **elija C++visual**   >  **MFC/ATL**. Si no los ve, use el Instalador de Visual Studio para agregarlos.
1. Elija **aplicación MFC** en el panel central.
1. Modifique los valores de configuración según sea necesario y, después, presione **Finalizar**.

Para obtener más información, vea [crear una aplicación MFC basada en formularios](creating-a-forms-based-mfc-application.md).

![Asistente para aplicaciones MFC](media/mfc-app-wizard.png)

## <a name="to-create-an-mfc-console-application"></a>Para crear una aplicación de consola MFC

Una aplicación de consola MFC es un programa de línea de comandos que usa las bibliotecas MFC, pero se ejecuta en la ventana de la consola.

1. En el menú principal, elija **archivo** > **nuevo** > **proyecto**.
1. En las plantillas instaladas, **elija C++ visual** > **escritorio de Windows**.
1. Elija **Asistente para escritorio de Windows** en el panel central.
1. Modifique el nombre del proyecto según sea necesario y, después, haga clic en **Aceptar** para abrir el **Asistente para escritorio de Windows**.
1. Active la casilla **encabezados de MFC** y establezca otros valores según sea necesario y, a continuación, presione **Finalizar**.

![Asistente para aplicaciones MFC](media/windows-desktop-wizard-2017.png)

::: moniker-end

::: moniker range="=vs-2015"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>Para crear una aplicación basada en cuadros de diálogo o formularios MFC

1. En el menú principal, elija **archivo** > **nuevo** > **proyecto**.
1. En las plantillas instaladas, **elija C++ visual** > **MFC**.
1. Elija **aplicación MFC** en el panel central.
1. Haga clic en **siguiente** para iniciar el **Asistente para aplicaciones MFC**.

Para obtener más información, vea [crear una aplicación MFC basada en formularios](creating-a-forms-based-mfc-application.md).

![Asistente para aplicaciones MFC](media/mfc-app-wizard-2015.png)

## <a name="to-create-an-mfc-console-application"></a>Para crear una aplicación de consola MFC

Una aplicación de consola MFC es un programa de línea de comandos que usa las bibliotecas MFC, pero se ejecuta en la ventana de la consola.

1. En el menú principal, elija **archivo** > **nuevo** > **proyecto**.
1. En las plantillas instaladas, **elija C++ visual** > **Win32**.
1. Elija **aplicación de consola Win32** en el panel central.
1. Modifique el nombre del proyecto según sea necesario y, a continuación, presione **Aceptar**.
1. En la segunda página del asistente, active la casilla **agregar encabezados comunes para MFC** y establezca otros valores según sea necesario y, a continuación, presione **Finalizar**.

::: moniker-end

Cuando se haya creado el proyecto, podrá ver los archivos creados en el **Explorador de soluciones**. Para obtener más información sobre los archivos que crea el asistente para el proyecto, vea el archivo Readme.txt generado por el proyecto. Para más información sobre los tipos de archivo, vea [Tipos de archivo creados para proyectos de C++ de Visual Studio](../../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Vea también

[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Páginas de propiedades](../../build/reference/property-pages-visual-cpp.md)