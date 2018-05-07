---
title: 'Cómo: realizar enlaces de datos de DDX y DDV con formularios Windows Forms | Documentos de Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2f6992aa0c7238d2dc89a8084c7b870dae23067a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>Cómo: Enlazar datos DDX/DDV con formularios Windows Forms
[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol) llamadas [CWinFormsControl:: CreateManagedControl](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol) para crear un control que coincida con el identificador de control de recurso. Si usa `DDX_ManagedControl` para un `CWinFormsControl` control (en el código generado asistente), no debe llamar `CreateManagedControl` explícitamente para el mismo control.  
  
 Llame a `DDX_ManagedControl` en [CWnd:: DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) para crear controles de identificadores de recursos. Para el intercambio de datos, no es necesario utilizar las funciones DDX/DDV con controles de formularios Windows Forms. En su lugar, puede colocar código para tener acceso a las propiedades del control administrado en el `DoDataExchange` método de la clase de cuadro de diálogo (o vista), como en el ejemplo siguiente.  
  
 En el ejemplo siguiente se muestra cómo enlazar una cadena de C++ nativo a un control de usuario. NET.  
  
## <a name="example"></a>Ejemplo  
 El siguiente es un ejemplo de enlace de datos DDX/DDV de una cadena MFC `m_str` con definido por el usuario `NameText` propiedad de un control de usuario. NET.  
  
 El control se crea cuando [CDialog:: OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) llamadas `CMyDlg::DoDataExchange` por primera vez, por lo que cualquier código que hace referencia a `m_UserControl` debe aparecer después de la `DDX_ManagedControl` llamar.  
  
 Puede implementar este código en la aplicación de MFC01 creada en [Cómo: crear el Control de usuario y el Host en un cuadro de diálogo](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).  
  
 Coloque el código siguiente en la declaración de CMFC01Dlg:  
  
```  
class CMFC01Dlg : public CDialog  
{  
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;  
   CString m_str;  
};  
```  
  
## <a name="example"></a>Ejemplo  
 Coloque el siguiente código en la implementación de CMFC01Dlg:  
  
```  
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
 Ahora agregaremos el método del controlador de hacer clic en el botón Aceptar. Haga clic en el **vista de recursos** ficha. En la vista de recursos, haga doble clic en `IDD_MFC01_DIALOG`. El recurso de cuadro de diálogo aparece en el Editor de recursos. A continuación, haga doble clic en el botón Aceptar...  
  
 Definir el controlador como se indica a continuación.  
  
```  
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
  
 Ahora puede compilar y ejecutar la aplicación. Tenga en cuenta que cualquier texto en el cuadro de texto se mostrará en un cuadro de mensaje emergente cuando se cierra la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Clase CWinFormsControl](../mfc/reference/cwinformscontrol-class.md)   
 [DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)   
 [CWnd:: DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)