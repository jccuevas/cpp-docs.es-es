---
title: Crear un control ActiveX MFC
ms.date: 09/12/2018
f1_keywords:
- vc.appwiz.activex.project
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
ms.assetid: 8bd5a93c-d04d-414e-bb28-163fdc1c0dd5
ms.openlocfilehash: b2dc48e2568e180820f8bca008c66878af4b575e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372301"
---
# <a name="creating-an-mfc-activex-control"></a>Crear un control ActiveX MFC

Los programas de control ActiveX son programas modulares diseñados para ofrecer un tipo específico de funcionalidad a una aplicación primaria. Por ejemplo, puede crear un control, como un botón, para utilizarlo en un cuadro de diálogo o una barra de herramientas para su uso en una página Web.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no se recomienda para nuevo desarrollo. Para obtener más información, consulte [controles ActiveX](../activex-controls.md).

La manera más fácil de crear un control ActiveX de MFC es utilizar el [Asistente para controles ActiveX de MFC](../../mfc/reference/mfc-activex-control-wizard.md).

### <a name="to-create-an-mfc-activex-control-using-the-mfc-activex-control-wizard"></a>Para crear un control ActiveX de MFC mediante el Asistente para controles ActiveX MFC

1. Siga las instrucciones del tema de Ayuda [cree un proyecto de aplicación de consola C++](../../get-started/tutorial-console-cpp.md).

1. En el **nuevo proyecto** cuadro de diálogo, seleccione el **ActiveX Control de MFC** icono en el panel Plantillas para abrir el Asistente para controles de ActiveX de MFC.

1. Definir la [configuración de la aplicación](../../mfc/reference/application-settings-mfc-activex-control-wizard.md), [nombres del control](../../mfc/reference/control-names-mfc-activex-control-wizard.md), y [controlar la configuración](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) mediante el Asistente para controles de ActiveX de MFC.

    > [!NOTE]
    >  Omita este paso para mantener la configuración predeterminada del asistente.

1. Haga clic en **finalizar** para cerrar el asistente y abrir el proyecto nuevo en el entorno de desarrollo.

Una vez haya creado el proyecto, puede ver los archivos creados en **el Explorador de soluciones**. Para obtener más información sobre los archivos que crea el asistente para el proyecto, vea el archivo Readme.txt generado por el proyecto. Para obtener más información acerca de los tipos de archivo, consulte [tipos de archivo creados para proyectos de Visual C++](../../build/reference/file-types-created-for-visual-cpp-projects.md).

Una vez haya creado el proyecto, puede usar los asistentes para código para agregar [funciones](../../ide/add-member-function-wizard.md), [variables](../../ide/add-member-variable-wizard.md), [eventos](../../ide/add-event-wizard.md), [propiedades](../../ide/names-add-property-wizard.md), y [métodos](../../ide/add-method-wizard.md). Para obtener más información acerca de cómo personalizar el control ActiveX, vea [controles ActiveX MFC](../../mfc/mfc-activex-controls.md).

## <a name="see-also"></a>Vea también

[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Páginas de propiedades](../../build/reference/property-pages-visual-cpp.md)

