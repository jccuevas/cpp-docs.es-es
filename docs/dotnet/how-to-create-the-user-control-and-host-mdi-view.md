---
title: 'Cómo: Crear el control de usuario y hospedarlo en una vista MDI'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
ms.openlocfilehash: 634dd9c1ad2ce9199cec0dfa7ef067bd45f242f6
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2019
ms.locfileid: "79544727"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>Cómo: Crear el control de usuario y hospedarlo en una vista MDI

Los pasos siguientes muestran cómo crear un control de usuario de .NET Framework, editarlo en una biblioteca de clases de control (específicamente un proyecto de la Biblioteca de controles de Windows) y, después, compilar el proyecto en un ensamblado. A continuación, el control se puede usar desde una aplicación MFC que utiliza clases derivadas de la [clase CView](../mfc/reference/cview-class.md) y de la [clase CWinFormsView](../mfc/reference/cwinformsview-class.md).

Para obtener información sobre cómo crear un control de usuario Windows Forms y crear una biblioteca de clases de control, vea [Cómo: crear controles de usuario](/dotnet/framework/winforms/controls/how-to-author-composite-controls).

> [!NOTE]
>  En algunos casos, puede que los controles de Windows Forms (por ejemplo, un control Grid de un tercero) no se comporten de forma confiable si se hospedan en una aplicación MFC. La solución recomendada es colocar un control de usuario de formularios Windows Forms en la aplicación MFC y el control Grid de un tercero dentro del control de usuario.

En este procedimiento se da por supuesto que ha creado un proyecto de biblioteca de controles Windows Forms denominado WindowsFormsControlLibrary1, según el procedimiento descrito en [Cómo: crear el control de usuario y el host en un cuadro de diálogo](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

### <a name="to-create-the-mfc-host-application"></a>Para crear la aplicación host MFC

1. Cree un proyecto de aplicación MFC.

   En el menú **archivo** , seleccione **nuevo**y, a continuación, haga clic en **proyecto**. En la **carpeta C++ visual** , seleccione **aplicación MFC**.

   En el cuadro **nombre** , escriba `MFC02` y cambie la configuración de la **solución** a **Agregar a solución**. Haga clic en **OK**.

   En el **Asistente para aplicaciones MFC**, acepte todos los valores predeterminados y, a continuación, haga clic en **Finalizar**. Esto crea una aplicación MFC con una interfaz de múltiples documentos.

1. Configure el proyecto para la compatibilidad con Common Language Runtime (CLR).

   En **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto `MFC01` y seleccione **propiedades** en el menú contextual. Aparece el cuadro de diálogo **páginas de propiedades** .

   En **propiedades de configuración**, seleccione **General**. En la sección **valores predeterminados del proyecto** , establezca **compatibilidad con Common Language Runtime** en **compatible con Common Language Runtime (/CLR)** .

   En **propiedades de configuración**, expanda **C/C++**  y haga clic en el nodo **General** . Establezca **formato de información de depuración** en **base de datos de programa (/Zi)** .

   Haga clic en el nodo **generación de código** . Establezca **Habilitar recompilación mínima** en **no (/GM-)** . Establezca también **comprobaciones básicas en tiempo de ejecución** en **predeterminado**.

   Haga clic en **Aceptar** para aplicar los cambios.

1. En *PCH. h* (*stdafx. h* en Visual Studio 2017 y versiones anteriores), agregue la línea siguiente:

    ```
    #using <System.Windows.Forms.dll>
    ```

1. Agregue una referencia al control .NET.

   En **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto `MFC02` y seleccione **Agregar**, **referencias**. En la **Página de propiedades**, haga clic en **Agregar nueva referencia**, seleccione WindowsFormsControlLibrary1 (en la pestaña **proyectos** ) y haga clic en **Aceptar**. Esto agrega una referencia en forma de opción del compilador [/Fu](../build/reference/fu-name-forced-hash-using-file.md) para que el programa se compile; también copia WindowsFormsControlLibrary1. dll en el directorio del proyecto `MFC02` para que se ejecute el programa.

1. En stdafx.h, encuentre esta línea:

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   Agregue estas líneas sobre ella:

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. Modifique la clase de vista para que herede de [CWinFormsView](../mfc/reference/cwinformsview-class.md).

   En MFC02View. h, reemplace [CView](../mfc/reference/cview-class.md) por [CWinFormsView](../mfc/reference/cwinformsview-class.md) para que el código aparezca como sigue:

    ```
    class CMFC02View : public CWinFormsView
    {
    };
    ```

   Si desea agregar vistas adicionales a su aplicación MDI, deberá llamar a [CWinApp:: AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) para cada vista que cree.

1. Modifique el archivo MFC02View.cpp para cambiar CView a CWinFormsView en la macro IMPLEMENT_DYNCREATE y en el mapa de mensajes, y reemplace el constructor vacío existente por el constructor que se muestra a continuación:

    ```
    IMPLEMENT_DYNCREATE(CMFC02View, CWinFormsView)

    CMFC02View::CMFC02View(): CWinFormsView(WindowsFormsControlLibrary1::UserControl1::typeid)
    {
    }
    BEGIN_MESSAGE_MAP(CMFC02View, CWinFormsView)
    //leave existing body as is
    END_MESSAGE_MAP()
    ```

1. Cree y ejecute el proyecto.

   En **Explorador de soluciones**, haga clic con el botón secundario en MFC02 y seleccione **establecer como proyecto de inicio**.

   En el menú **Compilar**, haga clic en **Compilar solución**.

   En el menú **depurar** , haga clic en **iniciar sin depurar**.

## <a name="see-also"></a>Consulte también

[Hospedar un control de usuario de Windows Forms como una vista de MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
