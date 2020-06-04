---
title: Hospedar un control de usuario de Windows Forms en un cuadro de diálogo MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 2704e04df3792edfee6c39f597fcbe71b6ce51b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374487"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>Hospedar un control de usuario de Windows Forms en un cuadro de diálogo MFC

MFC hospeda un control de formularios Windows Forms como un tipo especial de control ActiveX y <xref:System.Windows.Forms.Control> se comunica con el control mediante interfaces ActiveX y propiedades y métodos de la clase. Se recomienda usar propiedades y métodos de .NET Framework para operar en el control.

Para obtener una aplicación de ejemplo que muestra formularios Windows Forms utilizados con MFC, vea [Integración](https://www.microsoft.com/download/details.aspx?id=2113)de MFC y Windows Forms .

> [!NOTE]
> En la versión `CDialogBar` actual, un objeto no puede hospedar controles de formularios Windows Forms.

## <a name="in-this-section"></a>En esta sección

[Cómo: Crear el control de usuario y hospedarlo en un cuadro de diálogo](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[Cómo: Enlazar datos DDX/DDV con formularios Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[Cómo: Recibir eventos de Windows Forms de clases nativas de C++](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>Referencia

[Clase CWinFormsControl](../mfc/reference/cwinformscontrol-class.md) &#124; [Clase CDialog](../mfc/reference/cdialog-class.md) &#124; [clase CWnd](../mfc/reference/cwnd-class.md) &#124;<xref:System.Windows.Forms.Control>

## <a name="see-also"></a>Consulte también

[Usar un control de usuario de Windows Forms en MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Diferencias de programación de Windows Forms/MFC](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[Hospedar un control de usuario de Windows Forms como una vista de MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Hospedar un control de usuario de Windows Forms en un cuadro de diálogo MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
