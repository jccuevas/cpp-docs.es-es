---
title: Crear un control ActiveX MFC
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.activex.project
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
ms.assetid: 8bd5a93c-d04d-414e-bb28-163fdc1c0dd5
ms.openlocfilehash: d35b788910b0c73a3b6da85faf119958ffbccea0
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108438"
---
# <a name="creating-an-mfc-activex-control"></a>Crear un control ActiveX MFC

Los programas de control ActiveX son programas modulares diseñados para ofrecer un tipo específico de funcionalidad a una aplicación primaria. Por ejemplo, puede crear un control, como un botón, para utilizarlo en un cuadro de diálogo o una barra de herramientas para su uso en una página Web.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información, vea [controles ActiveX](../activex-controls.md).

La forma más fácil de crear un control ActiveX de MFC es usar el [Asistente para controles ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md).

### <a name="to-create-an-mfc-activex-control-using-the-mfc-activex-control-wizard"></a>Para crear un control ActiveX de MFC mediante el Asistente para controles ActiveX MFC

1. Siga las instrucciones del tema de ayuda [crear una aplicación MFC](creating-an-mfc-application.md) , pero elija **control ActiveX MFC** en la lista de plantillas disponibles.

1. Defina la [configuración](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)de la aplicación, [los nombres de los controles](../../mfc/reference/control-names-mfc-activex-control-wizard.md)y la [configuración del control](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) mediante el Asistente para controles ActiveX MFC.

    > [!NOTE]
    >  Omita este paso para mantener la configuración predeterminada del asistente.

1. Haga clic en **Finalizar** para cerrar el asistente y abrir el proyecto nuevo en el entorno de desarrollo.

Una vez creado el proyecto, puede ver los archivos creados en **Explorador de soluciones**. Para obtener más información sobre los archivos que crea el asistente para el proyecto, vea el archivo Readme.txt generado por el proyecto. Para más información sobre los tipos de archivo, vea [Tipos de archivo creados para proyectos de C++ de Visual Studio](../../build/reference/file-types-created-for-visual-cpp-projects.md).

Una vez creado el proyecto, puede usar los asistentes para código para agregar [funciones](../../ide/add-member-function-wizard.md), [variables](../../ide/add-member-variable-wizard.md), [eventos](../../ide/add-event-wizard.md), [propiedades](../../ide/names-add-property-wizard.md)y [métodos](../../ide/add-method-wizard.md). Para obtener más información sobre cómo personalizar el control ActiveX, vea [controles ActiveX MFC](../../mfc/mfc-activex-controls.md).

## <a name="see-also"></a>Vea también

[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Páginas de propiedades](../../build/reference/property-pages-visual-cpp.md)

