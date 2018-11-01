---
title: Hospedar un control de usuario de Windows Forms en un cuadro de diálogo MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 921e6fac32d37f8976d53d49adab72fb27ab5e99
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632224"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>Hospedar un control de usuario de Windows Forms en un cuadro de diálogo MFC

Hospeda un control de Windows Forms como un tipo especial de control ActiveX MFC y se comunica con el control mediante las interfaces ActiveX y las propiedades y métodos de la <xref:System.Windows.Forms.Control> clase. Se recomienda usar métodos y propiedades de .NET Framework para operar en el control.

Para una aplicación de ejemplo que muestra los formularios de Windows Forms utilizados con MFC, vea [integración de Windows Forms y MFC](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).

> [!NOTE]
>  En la versión actual, un `CDialogBar` objeto no puede hospedar controles de formularios Windows Forms.

## <a name="in-this-section"></a>En esta sección

[Cómo: Crear el control de usuario y el host en un cuadro de diálogo](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[Cómo: realizar el enlace de datos DDX/DDV con formularios de Windows](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[Cómo: Recibir eventos de Windows Forms de clases nativas de C++](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>Referencia

[CWinFormsControl (clase)](../mfc/reference/cwinformscontrol-class.md) &#124; [CDialog (clase)](../mfc/reference/cdialog-class.md) &#124; [clase CWnd](../mfc/reference/cwnd-class.md)&#124; <xref:System.Windows.Forms.Control>

## <a name="see-also"></a>Vea también

[Usar un control de usuario de Windows Forms en MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Diferencias de programación entre formularios Windows Forms y MFC](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[Hospedar un control de usuario de Windows Forms como una vista de MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Hospedar un control de usuario de Windows Forms como un cuadro de diálogo de MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)