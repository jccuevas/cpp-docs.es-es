---
title: 'Cómo: llamar a propiedades y métodos de los formularios Windows Forms controlan | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- method calls, Windows Forms
- calling methods, Windows Forms control
- calling properties, Windows Forms control
- Windows Forms controls [C++], methods
- calling properties
- Windows Forms controls [C++], properties
ms.assetid: 6e647d8a-fdaa-4aa1-b3fe-04f15cff8eb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1d3f8dc2251dbfbcd8155b0edc512a9dc40bacc2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393404"
---
# <a name="how-to-call-properties-and-methods-of-the-windows-forms-control"></a>Cómo: Llamar a propiedades y métodos del control de formularios Windows Forms

Dado que [:: GetControl](../mfc/reference/cwinformsview-class.md#getcontrol) devuelve un puntero a <xref:System.Windows.Forms.Control?displayProperty=fullName>y no un puntero a `WindowsControlLibrary1::UserControl1`, es aconsejable agregar un miembro del tipo de control de usuario e inicialícelo en [iView:: OnInitialUpdate ](../mfc/reference/iview-interface.md#oninitialupdate). Ahora puede llamar a métodos y propiedades mediante `m_ViewControl`.

En este tema se da por supuesto que ha completado previamente [Cómo: crear el Control de usuario y el Host en un cuadro de diálogo](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) y [Cómo: crear el Control de usuario y el Host en una vista MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

### <a name="to-create-the-mfc-host-application"></a>Para crear la aplicación host MFC

1. Abra la aplicación MFC que creó en [Cómo: crear el Control de usuario y el Host en una vista MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

1. Agregue la siguiente línea a la sección pública de invalidaciones de la `CMFC02View` declaración en MFC02View.h de clase.

     `gcroot<WindowsFormsControlLibrary1::UserControl1 ^> m_ViewControl;`

1. Agregue una invalidación para OnInitialupdate.

     Mostrar el **propiedades** ventana (F4). En **vista de clases** (CTRL + MAYÚS + C), seleccione la clase CMFC02View. En el **propiedades** ventana, seleccione el icono de invalidaciones. Desplácese por la lista a OnInitialUpdate. Haga clic en la lista desplegable y seleccione \<Agregar >. En MFC02View.cpp. Asegúrese de que el cuerpo de la función OnInitialUpdate es como sigue:

    ```
    CWinFormsView::OnInitialUpdate();
    m_ViewControl = safe_cast<WindowsFormsControlLibrary1::UserControl1 ^>(this->GetControl());
    m_ViewControl->textBox1->Text = gcnew System::String("hi");
    ```

1. Compile y ejecute el proyecto.

     En el menú **Compilar** , haga clic en **Compilar solución**.

     En el **depurar** menú, haga clic en **iniciar sin depurar**.

     Tenga en cuenta que ahora se inicializa el cuadro de texto.

## <a name="see-also"></a>Vea también

[Hospedar un control de usuario de Windows Forms como una vista de MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)