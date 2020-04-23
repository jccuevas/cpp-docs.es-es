---
title: 'Cómo: Hacer enlace de datos DDX-DDV con formularios Windows Forms'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
ms.openlocfilehash: 31629a4db2559112ba49f5c069b08de7abdfc2db
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754350"
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>Cómo: Enlazar datos DDX/DDV con formularios Windows Forms

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol) llama a [CWinFormsControl::CreateManagedControl](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol) para crear un control que coincida con el identificador de control de recursos. Si usa `DDX_ManagedControl` un `CWinFormsControl` control (en código generado por el `CreateManagedControl` asistente), no debe llamar explícitamente para el mismo control.

Llame `DDX_ManagedControl` a [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) para crear controles a partir de identificadores de recursos. Para el intercambio de datos, no es necesario utilizar las funciones DDX/DDV con controles de formularios Windows Forms. En su lugar, puede colocar código para tener `DoDataExchange` acceso a las propiedades del control administrado en el método de la clase de cuadro de diálogo (o vista), como en el ejemplo siguiente.

En el ejemplo siguiente se muestra cómo enlazar una cadena C++ nativa a un control de usuario de .NET.

## <a name="example"></a>Ejemplo

A continuación se muestra un ejemplo de enlace de `m_str` datos DDX/DDV de una cadena MFC con la propiedad definida por `NameText` el usuario de un control de usuario .NET.

El control se crea cuando [CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) llama `CMyDlg::DoDataExchange` por primera `m_UserControl` vez, `DDX_ManagedControl` por lo que cualquier código que hace referencia debe venir después de la llamada.

Puede implementar este código en la aplicación MFC01 que creó en [Cómo: crear el control](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)de usuario y host en un cuadro de diálogo .

Coloque el código siguiente en la declaración de CMFC01Dlg:

```
class CMFC01Dlg : public CDialog
{
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;
   CString m_str;
};
```

## <a name="example"></a>Ejemplo

Coloque el código siguiente en la implementación de CMFC01Dlg:

```cpp
void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)
{
   CDialog::DoDataExchange(pDX);
   DDX_ManagedControl(pDX, IDC_CTRL1, m_MyControl);

   if (pDX->m_bSaveAndValidate) {
      m_str = m_MyControl->textBox1->Text;
   } else
   {
      m_MyControl->textBox1->Text = gcnew System::String(m_str);
   }
}
```

## <a name="example"></a>Ejemplo

Ahora agregaremos el método de controlador para hacer clic en el botón Aceptar. Haga clic en la pestaña **Vista** de recursos. En la vista de `IDD_MFC01_DIALOG`recursos, haga doble clic en . El recurso de cuadro de diálogo aparece en el Editor de recursos. A continuación, haga doble clic en OK botón..

Defina el controlador de la siguiente manera.

```cpp
void CMFC01Dlg::OnBnClickedOk()
{
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));
   OnOK();
}
```

## <a name="example"></a>Ejemplo

Y agregue la siguiente línea a la implementación de BOOL CMFC01Dlg::OnInitDialog().

```
m_MyControl.GetControl()->textBox1->Text = "hello";
```

Ya puede compilar y ejecutar la aplicación. Observe que cualquier texto del cuadro de texto se mostrará en un cuadro de mensaje emergente cuando se cierre la aplicación.

## <a name="see-also"></a>Vea también

[CWinFormsControl (clase)](../mfc/reference/cwinformscontrol-class.md)<br/>
[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)<br/>
[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)
