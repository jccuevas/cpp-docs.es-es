---
title: "Hospedaje de Windows forman el Control de usuario como un cuadro de diálogo MFC | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], hosting as MFC Dialog
- hosting Windows Forms control [C++]
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7ad1d800619eb84a470dbc5e472e9191d13e8796
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>Hospedar un control de usuario de Windows Forms en un cuadro de diálogo MFC
MFC proporciona la clase de plantilla [CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md) por lo que puede hospedar un control de usuario de formularios Windows Forms (<xref:System.Windows.Forms.UserControl>) en un cuadro de diálogo MFC modal o no modal. `CWinFormsDialog`se deriva de la clase MFC [CDialog](../mfc/reference/cdialog-class.md), por lo que se puede iniciar el cuadro de diálogo modal o no modal.  
  
 El proceso que `CWinFormsDialog` utiliza para hospedar el control de usuario es similar al que se describe en [hospedar un Control de usuario de Windows Forms en un cuadro de diálogo de MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md). Sin embargo, `CWinFormsDialog` administra la inicialización y el hospedaje del control de usuario para que no tenga que programarse manualmente.  
  
 Para una aplicación de ejemplo que muestra formularios Windows Forms utilizados con MFC, vea [integración de Windows Forms y MFC](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
### <a name="to-create-the-mfc-host-application"></a>Para crear la aplicación host MFC  
  
1.  Cree un proyecto de aplicación MFC.  
  
     En el **archivo** menú, seleccione **New**y, a continuación, haga clic en **proyecto**. En el **Visual C++** carpeta, seleccione **aplicación MFC**.  
  
     En el **nombre** cuadro, escriba `MFC03` y cambiar la configuración de soluciones para **agregar a solución**. Haga clic en **Aceptar**.  
  
     En el **Asistente para aplicaciones MFC**, acepte todos los valores predeterminados y, a continuación, haga clic en **finalizar**. Esto crea una aplicación MFC con una interfaz de múltiples documentos.  
  
2.  Configurar el proyecto.  
  
     En **el Explorador de soluciones**, haga clic en el **MFC03** nodo de proyecto y elija **propiedades**. El **páginas de propiedades** aparece el cuadro de diálogo.  
  
     En el **páginas de propiedades** cuadro de diálogo, en la **propiedades de configuración** control de árbol, seleccione **General**, a continuación, en la **valorespredeterminadosdelproyecto**sección, establezca **compatible con Common Language Runtime** a **compatible con Common Language Runtime (/ clr)**. Haga clic en **Aceptar**.  
  
3.  Agregue una referencia al control .NET.  
  
     En **el Explorador de soluciones**, haga clic en el **MFC03** nodo de proyecto y elija **agregar**, **referencias**. En el **página de propiedades**, haga clic en **agregar nueva referencia**, seleccione WindowsControlLibrary1 (bajo la **proyectos** ficha) y haga clic en **Aceptar**. Esto agrega una referencia en forma de un [/FU](../build/reference/fu-name-forced-hash-using-file.md) opción del compilador para que el programa se compile; también copia WindowsControlLibrary1.dll en el `MFC03` directorio del proyecto para que el programa se ejecutará.  
  
4.  Agregar `#include <afxwinforms.h>` a stdafx.h, al final de la existente `#include` instrucciones.  
  
5.  Agregue una nueva clase que cree subclases `CDialog`.  
  
     Haga clic con el botón secundario en el nombre del proyecto y agregue una clase MFC (denominada CHostForWinForm) que cree subclases `CDialog`. Dado que no es necesario el recurso de cuadro de diálogo, puede eliminar el identificador de recurso (seleccione la vista de recursos, expanda la carpeta del cuadro de diálogo y elimine el recurso IDD_HOSTFORWINFORM.  A continuación, quite todas las referencias al identificador en el código.).  
  
6.  Reemplace `CDialog` en los archivos CHostForWinForm.h y CHostForWinForm.cpp con `CWinFormsDialog<WindowsControlLibrary1::UserControl1>`.  
  
7.  Llame a DoModal en la clase CHostForWinForm.  
  
     En MFC03.cpp, agregue `#include "HostForWinForm.h"`.  
  
     Antes de la instrucción return en la definición de CMFC03App:: InitInstance, agregue:  
  
     `CHostForWinForm m_HostForWinForm;`  
  
     `m_HostForWinForm.DoModal();`  
  
8.  Compile y ejecute el proyecto.  
  
     En el menú **Compilar** , haga clic en **Compilar solución**.  
  
     En el **depurar** menú, haga clic en **iniciar sin depurar**.  
  
     A continuación, agregará código para supervisar el estado de un control en los formularios Windows Forms desde la aplicación MFC.  
  
9. Agregue un controlador para OnInitDialog.  
  
     Mostrar la **propiedades** ventana (F4). En **vista de clases**, seleccione CHostForWinForm. En el **propiedades** ventana, seleccione invalida y en la fila correspondiente a OnInitDialog, haga clic en la columna izquierda y seleccione \< Agregar >. Esto agrega la siguiente línea a CHostForWinForm.h:  
  
    ```  
    virtual BOOL OnInitDialog();  
    ```  
  
10. Defina OnInitDialog (en CHostForWinForm.cpp) como sigue:  
  
    ```  
    BOOL CHostForWinForm::OnInitDialog() {  
       CWinFormsDialog<WindowsControlLibrary1::UserControl1>::OnInitDialog();  
       GetControl()->button1->Click += MAKE_DELEGATE(System::EventHandler, OnButton1);  
       return TRUE;  
    }  
    ```  
  
11. A continuación, agregue el controlador para OnButton1. Agregue las siguientes líneas a la sección pública de la clase CHostForWinForm en CHostForWinForm.h:  
  
    ```  
    virtual void OnButton1( System::Object^ sender, System::EventArgs^ e );  
  
    BEGIN_DELEGATE_MAP( CHostForWinForm )  
       EVENT_DELEGATE_ENTRY( OnButton1, System::Object^, System::EventArgs^ );  
    END_DELEGATE_MAP()  
    ```  
  
     En CHostForWinForm.cpp, agregue esta definición:  
  
    ```  
    void CHostForWinForm::OnButton1( System::Object^ sender, System::EventArgs^ e )   
    {  
       System::Windows::Forms::MessageBox::Show("test");  
    }  
    ```  
  
12. Compile y ejecute el proyecto. Al hacer clic en el botón, que se encuentra en el formulario Windows Forms, se ejecutará el código de la aplicación MFC.  
  
     A continuación, agregará código para mostrar el valor desde el código MFC en el cuadro de texto en el formulario Windows Forms.  
  
13. En la sección pública de la clase CHostForWinForm en CHostForWinForm.h, agregue la siguiente declaración:  
  
    ```  
    CString m_sEditBoxOnWinForm;  
    ```  
  
14. En la definición de DoDataExchange en CHostForWinForm.cpp, agregue las tres líneas siguientes al final de la función:  
  
    ```  
    if (pDX->m_bSaveAndValidate)  
       m_sEditBoxOnWinForm = CString( GetControl()->textBox1->Text);  
    else  
       GetControl()->textBox1->Text = gcnew System::String(m_sEditBoxOnWinForm);  
    ```  
  
15. En la definición de OnButton1 en CHostForWinForm.cpp, agregue las tres líneas siguientes al final de la función:  
  
    ```  
    this->UpdateData(TRUE);  
    System::String ^ z = gcnew System::String(m_sEditBoxOnWinForm);  
    System::Windows::Forms::MessageBox::Show(z);  
    ```  
  
16. Compile y ejecute el proyecto.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.Forms.UserControl?displayProperty=fullName>   
 [Usar un control de usuario de Windows Forms en MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)