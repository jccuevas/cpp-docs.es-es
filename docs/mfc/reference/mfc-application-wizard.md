---
title: Asistente para aplicaciones MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.overview
helpviewer_keywords:
- MFC Application Wizard
- executable files, creating
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
ms.openlocfilehash: 6949f136890e8274f225a49496b2eb1b8f78b6fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351831"
---
# <a name="mfc-application-wizard"></a>Asistente para aplicaciones MFC

El Asistente para aplicaciones MFC genera una aplicación que, al compilarse, implementa las características básicas de una aplicación ejecutable para Windows (.exe). La aplicación MFC inicial incluye archivos de código fuente de C++ (.cpp), archivos de recursos (.rc), archivos de encabezado (.h) y un archivo de proyecto (.vcxproj). El código generado en estos archivos iniciales se basa en MFC.

> [!NOTE]
> El asistente creará archivos adicionales para el proyecto en función de las opciones que seleccione. Por ejemplo, si selecciona **Ayuda contextual** en la página [Características avanzadas,](../../mfc/reference/advanced-features-mfc-application-wizard.md) el asistente crea los archivos necesarios para compilar los archivos de Ayuda del proyecto. Para obtener más información acerca de los archivos que crea el asistente, vea Tipos de archivo creados para proyectos de [Visual Studio C++](../../build/reference/file-types-created-for-visual-cpp-projects.md)y vea el archivo Readme.txt en el proyecto.

## <a name="overview"></a>Información general

En esta página del asistente se describe la configuración actual para la aplicación MFC que va a crear. De forma predeterminada, el asistente crea un proyecto de la manera siguiente:

- [Tipo de aplicación, Asistente para aplicaciones MFC](../../mfc/reference/application-type-mfc-application-wizard.md)

  - El proyecto se crea con compatibilidad con la interfaz de múltiples documentos (MDI) organizada por pestañas. Para obtener más información, consulte [SDI y MDI](../../mfc/sdi-and-mdi.md).

  - El proyecto utiliza la [arquitectura Document/View](../../mfc/document-view-architecture.md).

  - El proyecto utiliza las bibliotecas de Unicode.

  - El proyecto se crea utilizando el estilo de proyecto de Visual Studio y permite el cambio de estilos visuales.

  - El proyecto utiliza MFC en un archivo DLL compartido. Para obtener más información, vea Crear archivos DLL de [C/C++ en Visual Studio](../../build/dlls-in-visual-cpp.md).

- [Compatibilidad con documentos compuestos, Asistente para aplicaciones MFC](../../mfc/reference/compound-document-support-mfc-application-wizard.md)

  - El proyecto no proporciona compatibilidad con documentos compuestos.

- [Cadenas de plantilla de documento, Asistente para aplicaciones MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md)

  - El proyecto utiliza su nombre para las cadenas de plantillas de documentos predeterminadas.

- [Compatibilidad con bases de datos, Asistente para aplicaciones MFC](../../mfc/reference/database-support-mfc-application-wizard.md)

  - El proyecto no proporciona compatibilidad con bases de datos.

- [Características de la interfaz de usuario, Asistente para aplicaciones MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md)

  - El proyecto implementa características estándar de la interfaz de usuario de Windows, como un menú del sistema, una barra de estado, cuadros de maximización y minimización, un cuadro **Acerca** de, una barra de menús estándar y una barra de herramientas de acoplamiento y marcos secundarios.

- [Características avanzadas, Asistente para aplicaciones MFC](../../mfc/reference/advanced-features-mfc-application-wizard.md)

  - El proyecto ofrece compatibilidad con la impresión y la vista previa de impresión.

  - El proyecto admite controles ActiveX. Para obtener más información, vea [Secuencia de operaciones para crear controles ActiveX](../../mfc/sequence-of-operations-for-creating-activex-controls.md).

  - El proyecto no proporciona compatibilidad con [Automation](../../mfc/automation.md), [MAPI,](../../mfc/mapi-support-in-mfc.md) [Windows Sockets](../../mfc/windows-sockets-in-mfc.md)o Active Accessibility.

  - El proyecto admite un panel de acoplamiento **Explorer,** un panel de acoplamiento **de** salida y un panel de acoplamiento **Propiedades.**

- [Clases generadas, Asistente para aplicaciones MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md)

  - La clase de vista del proyecto se deriva de la [clase CView](../../mfc/reference/cview-class.md).

  - La clase de aplicación del proyecto se deriva de la [clase CWinAppEx](../../mfc/reference/cwinappex-class.md).

  - La clase de documento del proyecto se deriva de la [clase CDocument](../../mfc/reference/cdocument-class.md).

  - La clase de marco principal del proyecto se deriva de la [CMDIFrameWndEx (clase).](../../mfc/reference/cmdiframewndex-class.md)

  - La clase de marco secundario del proyecto se deriva de la [cmdichildwndEx (clase).](../../mfc/reference/cmdichildwndex-class.md)

Para cambiar esta configuración predeterminada, haga clic en el título de la pestaña correspondiente en la columna izquierda del asistente y realice las modificaciones en la página que aparece.

Después de crear un proyecto de aplicación MFC, puede agregar objetos o controles al proyecto mediante [asistentes](../../ide/adding-functionality-with-code-wizards-cpp.md)de código de Visual C++.

## <a name="see-also"></a>Consulte también

[Crear una aplicación MFC](../../mfc/reference/creating-an-mfc-application.md)<br/>
[Aplicaciones de escritorio de MFC](../../mfc/mfc-desktop-applications.md)<br/>
[Uso de las clases para escribir aplicaciones para Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)
