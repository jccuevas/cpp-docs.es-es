---
title: Hospedaje de un Windows forman el Control de usuario como un cuadro de diálogo MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], hosting as MFC Dialog
- hosting Windows Forms control [C++]
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 86a820e54e63c21c3ec4b9ace538bd6bfb4e9c0a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052871"
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>Hospedar un control de usuario de Windows Forms en un cuadro de diálogo MFC

MFC proporciona la clase de plantilla [CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md) por lo que puede hospedar un control de usuario de Windows Forms (<xref:System.Windows.Forms.UserControl>) en un cuadro de diálogo MFC modal o no modal. `CWinFormsDialog` se deriva de la clase MFC [CDialog](../mfc/reference/cdialog-class.md), por lo que el cuadro de diálogo se puede iniciar como modal o no modal.

El proceso que `CWinFormsDialog` utiliza para hospedar el control de usuario es similar al descrito en [hospedar un Control de usuario de Windows Forms en un cuadro de diálogo de MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md). Sin embargo, `CWinFormsDialog` administra la inicialización y el hospedaje del control de usuario para que no tenga que programarse manualmente.

Para una aplicación de ejemplo que muestra los formularios de Windows Forms utilizados con MFC, vea [integración de Windows Forms y MFC](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).

### <a name="to-create-the-mfc-host-application"></a>Para crear la aplicación host MFC

1. Cree un proyecto de aplicación MFC.

   En el **archivo** menú, seleccione **New**y, a continuación, haga clic en **proyecto**. En el **Visual C++** carpeta, seleccione **aplicación MFC**.

   En el **nombre** , escriba `MFC03` y cambie el valor de la solución a **agregar a solución**. Haga clic en **Aceptar**.

   En el **MFC Application Wizard**, acepte todos los valores predeterminados y, a continuación, haga clic en **finalizar**. Esto crea una aplicación MFC con una interfaz de múltiples documentos.

1. Configurar el proyecto.

   En **el Explorador de soluciones**, haga clic en el **MFC03** nodo de proyecto y elija **propiedades**. El **páginas de propiedades** aparece el cuadro de diálogo.

   En el **páginas de propiedades** cuadro de diálogo el **propiedades de configuración** control de árbol, seleccione **General**, a continuación, en el **valorespredeterminadosdelproyecto**sección, establezca **compatible con Common Language Runtime** a **compatible con Common Language Runtime (/ clr)**. Haga clic en **Aceptar**.

1. Agregue una referencia al control .NET.

   En **el Explorador de soluciones**, haga clic en el **MFC03** nodo de proyecto y elija **agregar**, **referencias**. En el **página de propiedades**, haga clic en **agregar nueva referencia**, seleccione WindowsControlLibrary1 (bajo la **proyectos** pestaña) y haga clic en **Aceptar**. Esto agrega una referencia en forma de un [/FU](../build/reference/fu-name-forced-hash-using-file.md) opción del compilador para que el programa se compile; también copiará WindowsControlLibrary1.dll en el `MFC03` directorio del proyecto para que el programa se ejecutará.

1. Agregar `#include <afxwinforms.h>` a stdafx.h al final de la existente `#include` instrucciones.

1. Agregue una clase nueva que cree subclases `CDialog`.

   Haga clic con el botón derecho en el nombre del proyecto y agregue una clase MFC (denominada CHostForWinForm) que cree subclases `CDialog`. Puesto que no es necesario el recurso de cuadro de diálogo, puede eliminar el identificador de recurso (seleccione **vista de recursos**, expanda el **diálogo** carpeta y eliminar `IDD_HOSTFORWINFORM` recursos.  A continuación, quite cualquier referencia al identificador en el código.).

1. Reemplace `CDialog` en los archivos CHostForWinForm.h y CHostForWinForm.cpp con `CWinFormsDialog<WindowsControlLibrary1::UserControl1>`.

1. Llame a DoModal en la clase CHostForWinForm.

   En MFC03.cpp, agregue `#include "HostForWinForm.h"`.

   Antes de la instrucción return en la definición de CMFC03App:: InitInstance, agregue:

    ```cpp
    CHostForWinForm m_HostForWinForm;
    m_HostForWinForm.DoModal();
    ```

1. Compile y ejecute el proyecto.

   En el menú **Compilar** , haga clic en **Compilar solución**.

   En el **depurar** menú, haga clic en **iniciar sin depurar**.

   A continuación agregará código para supervisar el estado de un control en los formularios de Windows de la aplicación MFC.

9. Agregue un controlador para OnInitDialog.

   Mostrar el **propiedades** ventana (F4). En **vista de clases**, seleccione CHostForWinForm. En el **propiedades** ventana, seleccione invalidaciones y en la fila correspondiente a OnInitDialog, haga clic en la columna izquierda y seleccione \< Agregar >. Esto agrega la línea siguiente a CHostForWinForm.h:

    ```cpp
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

12. Compile y ejecute el proyecto. Al hacer clic en el botón, que se encuentra en el formulario de Windows, se ejecutará el código de la aplicación MFC.

   A continuación agregará código para mostrar el valor desde el código de MFC en el cuadro de texto en el formulario de Windows.

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
[Uso de un Control de usuario de Windows Forms en MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)