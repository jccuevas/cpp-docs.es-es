---
title: "C&#243;mo: Enlazar datos DDX/DDV con formularios Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC [C++], alojar un control de formularios Windows Forms"
  - "formularios Windows Forms [C++], compatibilidad con MFC"
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# C&#243;mo: Enlazar datos DDX/DDV con formularios Windows Forms
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[DDX\_ManagedControl](../Topic/DDX_ManagedControl.md) llama a [CWinFormsControl::CreateManagedControl](../Topic/CWinFormsControl::CreateManagedControl.md) para crear un control que coincida con el identificador de control de recurso.  Si usa `DDX_ManagedControl` para un control `CWinFormsControl` \(en el código generado por el asistente\), no debería llamar a `CreateManagedControl` explícitamente para el mismo control.  
  
 Llame a `DDX_ManagedControl` en [CWnd::DoDataExchange](../Topic/CWnd::DoDataExchange.md) para crear controles a partir de identificadores de recursos.  Por lo que respecta al intercambio de datos, no es necesario utilizar las funciones DDX\/DDV con controles de formularios Windows Forms.  En su lugar, puede colocar código para tener acceso a las propiedades del control administrado en el método `DoDataExchange` de la clase de su cuadro de diálogo \(o vista\), como en el ejemplo siguiente.  
  
 El siguiente ejemplo muestra cómo enlazar una cadena de C\+\+ nativo a un control de usuario de .NET.  
  
## Ejemplo  
 A continuación, se muestra un ejemplo del enlace de datos de DDX\/DDV de una cadena MFC `m_str` con la propiedad `NameText` definida por el usuario de un control de usuario de .NET.  
  
 El control se crea cuando [CDialog::OnInitDialog](../Topic/CDialog::OnInitDialog.md) llama por primera vez a `CMyDlg::DoDataExchange`; por tanto, cualquier código que haga referencia a `m_UserControl` debe ir detrás de la llamada a `DDX_ManagedControl`.  
  
 Puede implementar este código en la aplicación de MFC01 creada en [Cómo: Crear el control de usuario y hospedarlo en un cuadro de diálogo](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).  
  
 Coloque el código siguiente en la declaración de CMFC01Dlg:  
  
```  
class CMFC01Dlg : public CDialog  
{  
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;  
   CString m_str;  
};  
```  
  
## Ejemplo  
 Coloque el código siguiente en la implementación de CMFC01Dlg:  
  
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
  
## Ejemplo  
 Ahora agregaremos el método controlador para un evento clic en el botón Aceptar.  Haga clic en la ficha **Vista de recursos**.  En la Vista de recursos, haga doble clic en `IDD_MFC01_DIALOG`.  Aparece el recurso de cuadro de diálogo en el Editor de recursos.  A continuación, haga doble clic en el botón Aceptar.  
  
 Defina el controlador del modo siguiente.  
  
```  
void CMFC01Dlg::OnBnClickedOk()  
{  
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));  
   OnOK();  
}  
```  
  
## Ejemplo  
 Y agregue la línea siguiente a la implementación de BOOL CMFC01Dlg::OnInitDialog \(\).  
  
```  
m_MyControl.GetControl()->textBox1->Text = "hello";  
```  
  
 Ahora ya puede compilar y ejecutar la aplicación.  Observe que los textos del cuadro de texto se mostrarán en un cuadro de mensajes emergente cuando se cierre la aplicación.  
  
## Vea también  
 [CWinFormsControl Class](../mfc/reference/cwinformscontrol-class.md)   
 [DDX\_ManagedControl](../Topic/DDX_ManagedControl.md)   
 [CWnd::DoDataExchange](../Topic/CWnd::DoDataExchange.md)