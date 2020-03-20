---
title: Hospedar un control de usuario de Windows Forms en un cuadro de diálogo MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], hosting as MFC Dialog
- hosting Windows Forms control [C++]
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
ms.openlocfilehash: 7fc2aad1e0a550fb8f22b311518ae9fb16c076a5
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "79544800"
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>Hospedar un control de usuario de Windows Forms en un cuadro de diálogo MFC

MFC proporciona la clase de plantilla [CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md) para que pueda hospedar un Windows Forms control de usuario (<xref:System.Windows.Forms.UserControl>) en un cuadro de diálogo de MFC modal o no modal. `CWinFormsDialog` se deriva de la clase MFC [CDialog](../mfc/reference/cdialog-class.md), por lo que el cuadro de diálogo se puede iniciar como modal o no modal.

El proceso que `CWinFormsDialog` usa para hospedar el control de usuario es similar al que se describe en [alojar un control de usuario de Windows Forms en un cuadro de diálogo de MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md). Sin embargo, `CWinFormsDialog` administra la inicialización y el hospedaje del control de usuario para que no tenga que programarse manualmente.

Para obtener una aplicación de ejemplo que muestra Windows Forms se usa con MFC, vea [integración de MFC y Windows Forms](https://www.microsoft.com/download/details.aspx?id=2113).

### <a name="to-create-the-mfc-host-application"></a>Para crear la aplicación host MFC

1. Cree un proyecto de aplicación MFC.

   En el menú **archivo** , seleccione **nuevo**y, a continuación, haga clic en **proyecto**. En la **carpeta C++ visual** , seleccione **aplicación MFC**.

   En el cuadro **nombre** , escriba `MFC03` y cambie la configuración de la solución a **Agregar a solución**. Haga clic en **Aceptar**.

   En el **Asistente para aplicaciones MFC**, acepte todos los valores predeterminados y, a continuación, haga clic en **Finalizar**. Esto crea una aplicación MFC con una interfaz de múltiples documentos.

1. Configure el proyecto.

   En **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto **MFC03** y elija **propiedades**. Aparece el cuadro de diálogo **páginas de propiedades** .

   En el cuadro de diálogo **páginas de propiedades** , en el control de árbol **propiedades de configuración** , seleccione **General**y, a continuación, en la sección **valores predeterminados del proyecto** , establezca **compatibilidad con Common Language Runtime** en **compatible con Common Language Runtime (/CLR)** . Haga clic en **OK**.

1. Agregue una referencia al control .NET.

   En **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto **MFC03** y elija **Agregar**, **referencias**. En la **Página de propiedades**, haga clic en **Agregar nueva referencia**, seleccione WindowsControlLibrary1 (en la pestaña **proyectos** ) y haga clic en **Aceptar**. Esto agrega una referencia en forma de opción del compilador [/Fu](../build/reference/fu-name-forced-hash-using-file.md) para que el programa se compile; también copia WindowsControlLibrary1. dll en el directorio del proyecto `MFC03` para que se ejecute el programa.

1. Agregue `#include <afxwinforms.h>` a *PCH. h* (*stdafx. h* en Visual Studio 2017 y versiones anteriores), al final de las instrucciones de `#include` existentes.

1. Agregue una nueva clase que subclases `CDialog`.

   Haga clic con el botón derecho en el nombre del proyecto y agregue una clase MFC (denominada CHostForWinForm) que subclases `CDialog`. Dado que no necesita el recurso de cuadro de diálogo, puede eliminar el identificador de recurso (seleccione **vista de recursos**, expandir la carpeta de cuadro de **diálogo** y eliminar `IDD_HOSTFORWINFORM` recurso.  A continuación, quite todas las referencias al identificador en el código).

1. Reemplace `CDialog` en los archivos CHostForWinForm. h y CHostForWinForm. cpp por `CWinFormsDialog<WindowsControlLibrary1::UserControl1>`.

1. Llame a DoModal en la clase CHostForWinForm.

   En MFC03. cpp, agregue `#include "HostForWinForm.h"`.

   Antes de la instrucción return en la definición de CMFC03App:: InitInstance, agregue:

    ```cpp
    CHostForWinForm m_HostForWinForm;
    m_HostForWinForm.DoModal();
    ```

1. Cree y ejecute el proyecto.

   En el menú **Compilar**, haga clic en **Compilar solución**.

   En el menú **depurar** , haga clic en **iniciar sin depurar**.

   A continuación, agregará código para supervisar el estado de un control en el Windows Forms desde la aplicación MFC.

1. Agregue un controlador para OnInitDialog.

   Mostrar la ventana **propiedades** (F4). En **vista de clases**, seleccione CHostForWinForm. En la ventana **propiedades** , seleccione invalidaciones y, en la fila de OnInitDialog, haga clic en la columna izquierda y seleccione \< agregar >. Esto agrega la siguiente línea a CHostForWinForm. h:

    ```cpp
    virtual BOOL OnInitDialog();
    ```

1. Defina OnInitDialog (en CHostForWinForm. cpp) de la manera siguiente:

    ```cpp
    BOOL CHostForWinForm::OnInitDialog() {
       CWinFormsDialog<WindowsControlLibrary1::UserControl1>::OnInitDialog();
       GetControl()->button1->Click += MAKE_DELEGATE(System::EventHandler, OnButton1);
       return TRUE;
    }
    ```

1. A continuación, agregue el controlador OnButton1. Agregue las líneas siguientes a la sección pública de la clase CHostForWinForm en CHostForWinForm. h:

    ```cpp
    virtual void OnButton1( System::Object^ sender, System::EventArgs^ e );

    BEGIN_DELEGATE_MAP( CHostForWinForm )
       EVENT_DELEGATE_ENTRY( OnButton1, System::Object^, System::EventArgs^ );
    END_DELEGATE_MAP()
    ```

   En CHostForWinForm. cpp, agregue esta definición:

    ```cpp
    void CHostForWinForm::OnButton1( System::Object^ sender, System::EventArgs^ e )
    {
       System::Windows::Forms::MessageBox::Show("test");
    }
    ```

1. Cree y ejecute el proyecto. Al hacer clic en el botón, que se encuentra en Windows Form, se ejecutará el código en la aplicación MFC.

    A continuación, agregará código para mostrar desde el código MFC el valor en el cuadro de texto del formulario de Windows Forms.

1. En la sección pública de la clase CHostForWinForm en CHostForWinForm. h, agregue la siguiente declaración:

    ```cpp
    CString m_sEditBoxOnWinForm;
    ```

1. En la definición de DoDataExchange en CHostForWinForm. cpp, agregue las tres líneas siguientes al final de la función:

    ```cpp
    if (pDX->m_bSaveAndValidate)
       m_sEditBoxOnWinForm = CString( GetControl()->textBox1->Text);
    else
       GetControl()->textBox1->Text = gcnew System::String(m_sEditBoxOnWinForm);
    ```

1. En la definición de OnButton1 en CHostForWinForm. cpp, agregue las tres líneas siguientes al final de la función:

    ```cpp
    this->UpdateData(TRUE);
    System::String ^ z = gcnew System::String(m_sEditBoxOnWinForm);
    System::Windows::Forms::MessageBox::Show(z);
    ```

1. Cree y ejecute el proyecto.

## <a name="see-also"></a>Consulte también

<xref:System.Windows.Forms.UserControl?displayProperty=fullName>
[mediante un control de usuario de Windows Forms en MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)
