---
title: Agregar un cuadro de diálogo ATL
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding dialog resources
- MFC dialog boxes, ATL dialogs
- dialog boxes, ATL
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
ms.openlocfilehash: ee6f6b1b83c625b30b601275084550309e0e7c68
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495373"
---
# <a name="adding-an-atl-dialog-box"></a>Agregar un cuadro de diálogo ATL

Para agregar un cuadro de diálogo ATL al proyecto, el proyecto debe ser un proyecto ATL o un proyecto MFC que incluye compatibilidad con ATL. Puede usar el [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md) para crear una aplicación ATL, o bien [agregar un objeto ATL a una aplicación MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad con ATL para una aplicación MFC.

De forma predeterminada, el Asistente de cuadro de diálogo ATL implementa un cuadro de diálogo derivado de [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Esta clase incluye compatibilidad para hospedar controles ActiveX y Windows. Si no desea la sobrecarga de la compatibilidad con el control ActiveX, una vez que el asistente ha generado el código, reemplace todas las instancias de `CAxDialogImpl` con cualquiera [CSimpleDialog](../../atl/reference/csimpledialog-class.md) o [CDialogImpl](../../atl/reference/cdialogimpl-class.md) como clase base .

> [!NOTE]
> `CSimpleDialog` crea los cuadros de diálogo modales que admiten únicamente controles comunes de Windows. `CDialogImpl` crea los cuadros de diálogo modal o no modal.

## <a name="to-add-an-atl-dialog-resource-to-your-project"></a>Para agregar un recurso de cuadro de diálogo ATL al proyecto

1. Cree un proyecto ATL mediante el [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md).

1. Desde [vista de clases](/visualstudio/ide/viewing-the-structure-of-code), haga clic en el nombre del proyecto y haga clic en **agregar** en el menú contextual. Haga clic en **Agregar clase**.

1. En el **plantillas** panel de la [Agregar clase](../../ide/add-class-dialog-box.md) cuadro de diálogo, haga clic en **cuadro de diálogo ATL**. Haga clic en **abierto** para mostrar el [Asistente del cuadro de diálogo ATL](../../atl/reference/atl-dialog-wizard.md).

Para obtener más información, consulte [implementa un cuadro de diálogo](../../atl/implementing-a-dialog-box.md).

## <a name="see-also"></a>Vea también

[Agregar una clase](../../ide/adding-a-class-visual-cpp.md)<br/>
[Clases de ventana](../../atl/atl-window-classes.md)<br/>
[Mapas de mensajes](../../atl/message-maps-atl.md)
