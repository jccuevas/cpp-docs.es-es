---
title: Asistente para aplicaciones MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.overview
helpviewer_keywords:
- MFC Application Wizard
- executable files, creating
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
ms.openlocfilehash: 3cdaba750060290fa25007d4097b6782d6f20fbf
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258637"
---
# <a name="mfc-application-wizard"></a>Asistente para aplicaciones MFC

El Asistente para aplicaciones MFC genera una aplicación que, al compilarse, implementa las características básicas de una aplicación ejecutable para Windows (.exe). La aplicación MFC inicial incluye archivos de código fuente de C++ (.cpp), archivos de recursos (.rc), archivos de encabezado (.h) y un archivo de proyecto (.vcxproj). El código generado en estos archivos iniciales se basa en MFC.

> [!NOTE]
>  El asistente creará archivos adicionales para el proyecto en función de las opciones que seleccione. Por ejemplo, si selecciona **ayuda contextual** en el [características avanzadas](../../mfc/reference/advanced-features-mfc-application-wizard.md) página, el asistente crea los archivos que son necesarios para compilar los archivos de Ayuda del proyecto. Para obtener más información acerca de los archivos que crea el asistente, consulte [tipos de archivo creados para proyectos de Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md)y consulte el archivo Readme.txt del proyecto.

## <a name="overview"></a>Información general

En esta página del asistente se describe la configuración actual para la aplicación MFC que va a crear. De forma predeterminada, el asistente crea un proyecto de la manera siguiente:

- [Tipo de aplicación, Asistente para aplicaciones MFC](../../mfc/reference/application-type-mfc-application-wizard.md)

   - El proyecto se crea con compatibilidad con la interfaz de múltiples documentos (MDI) organizada por pestañas. Para obtener más información, consulte [SDI y MDI](../../mfc/sdi-and-mdi.md).

   - El proyecto usa el [arquitectura documento/vista](../../mfc/document-view-architecture.md).

   - El proyecto utiliza las bibliotecas de Unicode.

   - El proyecto se crea utilizando el estilo de proyecto de Visual Studio y permite el cambio de estilos visuales.

   - El proyecto utiliza MFC en un archivo DLL compartido. Para más información, vea [DLLs in Visual C++](../../build/dlls-in-visual-cpp.md) (DLL en Visual C++).

- [Compatibilidad con documentos compuestos, Asistente para aplicaciones MFC](../../mfc/reference/compound-document-support-mfc-application-wizard.md)

   - El proyecto no proporciona compatibilidad con documentos compuestos.

- [Cadenas de plantillas de documentos, Asistente para aplicaciones MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md)

   - El proyecto utiliza su nombre para las cadenas de plantillas de documentos predeterminadas.

- [Compatibilidad con bases de datos, Asistente para aplicaciones MFC](../../mfc/reference/database-support-mfc-application-wizard.md)

   - El proyecto no proporciona compatibilidad con bases de datos.

- [Características de la interfaz de usuario, Asistente para aplicaciones MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md)

   - El proyecto implementa características como un menú de sistema, una barra de estado, maximizar y minimizar los cuadros, la interfaz de usuario de Windows estándar un **sobre** cuadro, una barra de menús estándar y acoplamiento de barra de herramientas y marcos secundarios.

- [Características avanzadas, Asistente para aplicaciones MFC](../../mfc/reference/advanced-features-mfc-application-wizard.md)

   - El proyecto ofrece compatibilidad con la impresión y la vista previa de impresión.

   - El proyecto admite controles ActiveX. Para obtener más información, consulte [secuencia de operaciones para crear controles ActiveX](../../mfc/sequence-of-operations-for-creating-activex-controls.md).

   - El proyecto no proporciona compatibilidad con [automatización](../../mfc/automation.md), [MAPI](../../mfc/mapi-support-in-mfc.md), [Windows Sockets](../../mfc/windows-sockets-in-mfc.md), ni Active Accessibility.

   - El proyecto admite un **Explorer** panel acoplable, un **salida** panel acoplable y un **propiedades** panel acoplable.

- [Clases generadas, Asistente para aplicaciones MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md)

   - Clase de vista del proyecto se deriva el [clase CView](../../mfc/reference/cview-class.md).

   - Clase de aplicación del proyecto se deriva el [CWinAppEx (clase)](../../mfc/reference/cwinappex-class.md).

   - Clase de documento del proyecto se deriva el [CDocument (clase)](../../mfc/reference/cdocument-class.md).

   - Clase de marco principal del proyecto se deriva el [CMDIFrameWndEx (clase)](../../mfc/reference/cmdiframewndex-class.md).

   - Clase de marco secundario del proyecto se deriva el [CMDIChildWndEx (clase)](../../mfc/reference/cmdichildwndex-class.md).

Para cambiar esta configuración predeterminada, haga clic en el título de la pestaña correspondiente en la columna izquierda del asistente y realice las modificaciones en la página que aparece.

Después de crear un proyecto de aplicación MFC, puede agregar objetos o controles al proyecto mediante Visual C++ [asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md).

## <a name="see-also"></a>Vea también

[Creación de una aplicación MFC](../../mfc/reference/creating-an-mfc-application.md)<br/>
[Aplicaciones de escritorio de MFC](../../mfc/mfc-desktop-applications.md)<br/>
[Uso de las clases para escribir aplicaciones para Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)
