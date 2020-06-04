---
title: Hospedar un control de usuario de Windows Forms como vista de MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms controls [C++], hosting as an MFC view
- hosting Windows Forms control [C++]
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
ms.openlocfilehash: bf91730f98685935d50ee0076739b436e8d9da60
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "79544788"
---
# <a name="hosting-a-windows-forms-user-control-as-an-mfc-view"></a>Hospedar un control de usuario de Windows Forms como vista de MFC

MFC utiliza la clase CWinFormsView para hospedar un control de usuario Windows Forms en una vista MFC. Las vistas de Windows Forms MFC son controles ActiveX. El control de usuario se hospeda como elemento secundario de la vista nativa y ocupa todo el área cliente de la vista nativa.

El resultado final es similar al modelo usado por la [clase CFormView](../mfc/reference/cformview-class.md). Esto le permite aprovechar el diseñador de Windows Forms y el tiempo de ejecución para crear vistas basadas en formularios enriquecidas.

Dado que las vistas de Windows Forms MFC son controles ActiveX, no tienen el mismo `hwnd` que las vistas MFC. Tampoco se pueden pasar como un puntero a una vista [CView](../mfc/reference/cview-class.md) . En general, utilice métodos .NET Framework para trabajar con vistas de Windows Forms y confiar menos en Win32.

Para obtener una aplicación de ejemplo que muestra Windows Forms se usa con MFC, vea [integración de MFC y Windows Forms](https://www.microsoft.com/download/details.aspx?id=2113).

## <a name="in-this-section"></a>En esta sección

[Cómo: Crear el control de usuario y hospedarlo en una vista MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)

[Cómo: Agregar enrutamientos de comandos al control de Windows Forms](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)

[Cómo: Llamar a propiedades y métodos del control de formularios Windows Forms](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)

## <a name="see-also"></a>Consulte también

[Usar un control de usuario de Windows Forms en MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Cómo: Crear controles compuestos](/dotnet/framework/winforms/controls/how-to-author-composite-controls)
