---
title: Hospedar un control de usuario de Windows Forms en un cuadro de diálogo MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 8925b86a5920df6a53a2625b782cf41e1a7fe32c
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "79544794"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>Hospedar un control de usuario de Windows Forms en un cuadro de diálogo MFC

MFC hospeda un control de Windows Forms como un tipo especial de control ActiveX y se comunica con el control mediante el uso de interfaces ActiveX, y propiedades y métodos de la clase <xref:System.Windows.Forms.Control>. Se recomienda usar las propiedades y los métodos de .NET Framework para operar en el control.

Para obtener una aplicación de ejemplo que muestra Windows Forms se usa con MFC, vea [integración de MFC y Windows Forms](https://www.microsoft.com/download/details.aspx?id=2113).

> [!NOTE]
>  En la versión actual, un objeto de `CDialogBar` no puede hospedar controles de Windows Forms.

## <a name="in-this-section"></a>En esta sección

[Cómo: Crear el control de usuario y el host en un cuadro de diálogo](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[Cómo: realizar el enlace de datos DDX/DDV con Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[Cómo: Recibir eventos de Windows Forms de clases nativas de C++](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>Referencia

&#124; Clase [CWinFormsControl](../mfc/reference/cwinformscontrol-class.md) clase [CDialog](../mfc/reference/cdialog-class.md) &#124; clase [CWnd](../mfc/reference/cwnd-class.md) &#124; <xref:System.Windows.Forms.Control>

## <a name="see-also"></a>Consulte también

[Usar un control de usuario de Windows Forms en MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Diferencias de programación entre formularios Windows Forms y MFC](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[Hospedar un control de usuario de Windows Forms como una vista de MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Hospedar un control de usuario de Windows Forms como un cuadro de diálogo de MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
