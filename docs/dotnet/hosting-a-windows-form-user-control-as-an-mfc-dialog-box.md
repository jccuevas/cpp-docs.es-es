---
title: "Hospedar un control de usuario de Windows Forms en un cuadro de di&#225;logo MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hospedar un control de formularios Windows Forms [C++]"
  - "MFC [C++], compatibilidad con formularios Windows Forms"
  - "formularios Windows Forms [C++], hospedar como cuadro de diálogo MFC"
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Hospedar un control de usuario de Windows Forms en un cuadro de di&#225;logo MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC proporciona la clase de plantilla [CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md) para permitir hospedar un control de usuario de Windows Forms \(<xref:System.Windows.Forms.UserControl>\) en un cuadro de diálogo de MFC modal o no modal.  `CWinFormsDialog` deriva de la clase MFC [CDialog](../mfc/reference/cdialog-class.md), por lo que el cuadro de diálogo se puede iniciar como modal o no modal.  
  
 El proceso que utiliza `CWinFormsDialog` para hospedar el control de usuario es similar al descrito en [Hospedar un control de usuario de Windows Forms en un cuadro de diálogo MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md).  Sin embargo, `CWinFormsDialog` administra la inicialización y el hospedaje del control de usuario para que no tenga que programarse manualmente.  
  
 Para obtener una aplicación de ejemplo que muestra el uso de Windows Forms con MFC, vea [Integración de MFC y Windows Forms](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
### Para crear la aplicación host MFC  
  
1.  Cree un proyecto de aplicación MFC.  
  
     En el menú **Archivo**, seleccione **Nuevo** y, a continuación, haga clic en **Proyecto**.  En la carpeta **Visual C\+\+**, seleccione **Aplicación MFC**.  
  
     En el cuadro **Nombre**, escriba `MFC03` y cambie el valor Solución a **Agregar a solución**.Haga clic en **Aceptar**.  
  
     En el **Asistente para aplicaciones MFC**, acepte todos los valores predeterminados y, a continuación, haga clic en **Finalizar**.  Esto crea una aplicación MFC con una interfaz de múltiples documentos.  
  
2.  Configure el proyecto.  
  
     En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto **MFC03** y elija **Propiedades**.  Aparecerá el cuadro de diálogo **Páginas de propiedades**.  
  
     En el cuadro de diálogo **Páginas de propiedades**, en el control de árbol **Propiedades de configuración**, seleccione **Generales**, a continuación, en la sección **Valores predeterminados del proyecto**, establezca **Compatibilidad con Common Language Runtime** en **Compatible con Common Language Runtime \(\/clr\)**.  Haga clic en **Aceptar**.  
  
3.  Agregue una referencia al control .NET.  
  
     En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto **MFC03** y, a continuación, elija **Agregar**, **Referencias**.  En la **Página de propiedades**, haga clic en **Agregar nueva referencia**, seleccione WindowsControlLibrary1 \(bajo la ficha **Proyectos**\) y haga clic en **Aceptar**.  Así se agregará una referencia en forma de una opción del compilador [\/FU](../build/reference/fu-name-forced-hash-using-file.md) para que el programa compile; también copiará WindowsControlLibrary1.dll en el directorio del proyecto `MFC03` para que se ejecute el programa.  
  
4.  Agregue `#include <afxwinforms.h>` a stdafx.h al final de las instrucciones `#include` existentes.  
  
5.  Agregue una nueva clase que cree subclases `CDialog`.  
  
     Haga clic con el botón secundario del mouse en el nombre del proyecto y agregue una clase MFC \(denominada CHostForWinForm\) que cree subclases `CDialog`.  Como no se necesita el recurso de cuadro de diálogo, se puede eliminar el identificador de recursos \(seleccione la Vista de recursos, expanda la carpeta Cuadro de diálogo y elimine el recurso IDD\_HOSTFORWINFORM.  A continuación, quite cualquier referencia al identificador en el código.\).  
  
6.  Reemplace `CDialog` en los archivos CHostForWinForm.h y CHostForWinForm.cpp por `CWinFormsDialog<WindowsControlLibrary1::UserControl1>`.  
  
7.  Llame a DoModal en la clase CHostForWinForm.  
  
     En MFC03.cpp, agregue `#include "HostForWinForm.h"`.  
  
     Delante de la instrucción return en la definición de CMFC03App::InitInstance, agregue:  
  
     `CHostForWinForm m_HostForWinForm;`  
  
     `m_HostForWinForm.DoModal();`  
  
8.  Compile y ejecute el proyecto.  
  
     En el menú **Compilar**, haga clic en **Compilar solución**.  
  
     En el menú **Depurar**, haga clic en **Iniciar sin depurar**.  
  
     Después agregará código para supervisar el estado de un control en los formularios Windows Forms de la aplicación MFC.  
  
9. Agregue un controlador para OnInitDialog.  
  
     Muestre la ventana **Propiedades** \(F4\).  En la **Vista de clases**, seleccione CHostForWinForm.  En la ventana **Propiedades**, seleccione Reemplazos y en la fila correspondiente a OnInitDialog, haga clic en la columna de la izquierda y seleccione \< Add \>.  Con esta acción se agrega la línea siguiente a CHostForWinForm.h:  
  
    ```  
    virtual BOOL OnInitDialog();  
    ```  
  
10. Defina OnInitDialog \(en CHostForWinForm.cpp\) del modo siguiente:  
  
    ```  
    BOOL CHostForWinForm::OnInitDialog() {  
       CWinFormsDialog<WindowsControlLibrary1::UserControl1>::OnInitDialog();  
       GetControl()->button1->Click += MAKE_DELEGATE(System::EventHandler, OnButton1);  
       return TRUE;  
    }  
    ```  
  
11. A continuación, agregue el controlador para OnButton1.  Agregue las líneas siguientes a la sección pública de la clase CHostForWinForm en CHostForWinForm.h:  
  
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
  
12. Compile y ejecute el proyecto.  Cuando haga clic en el botón, que está en el Windows Form, se ejecutará el código en la aplicación MFC.  
  
     Después agregará código para que, desde el código de MFC, se muestre el valor en el cuadro de texto del Windows Form.  
  
13. En la sección pública de la clase CHostForWinForm en CHostForWinForm.h, agregue la declaración siguiente:  
  
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
  
## Vea también  
 <xref:System.Windows.Forms.UserControl?displayProperty=fullName>   
 [Utilizar un control de usuario de Windows Forms en MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)