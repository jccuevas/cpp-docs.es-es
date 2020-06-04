---
title: 'Cómo: Crear el control de usuario y hospedarlo en una vista MDI'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
ms.openlocfilehash: 72501ba32d3b8b9a5c5fd8dd0c56f0628642b147
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374468"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>Cómo: Crear el control de usuario y hospedarlo en una vista MDI

Los pasos siguientes muestran cómo crear un control de usuario de .NET Framework, editarlo en una biblioteca de clases de control (específicamente un proyecto de la Biblioteca de controles de Windows) y, después, compilar el proyecto en un ensamblado. A continuación, el control se puede consumir desde una aplicación MFC que utiliza clases derivadas de [CView (Clase)](../mfc/reference/cview-class.md) y [CWinFormsView (clase).](../mfc/reference/cwinformsview-class.md)

Para obtener información acerca de cómo crear un control de usuario de formularios Windows Forms y crear una biblioteca de clases de control, vea [Cómo: Crear controles](/dotnet/framework/winforms/controls/how-to-author-composite-controls)de usuario .

> [!NOTE]
> En algunos casos, puede que los controles de Windows Forms (por ejemplo, un control Grid de un tercero) no se comporten de forma confiable si se hospedan en una aplicación MFC. La solución recomendada es colocar un control de usuario de formularios Windows Forms en la aplicación MFC y el control Grid de un tercero dentro del control de usuario.

En este procedimiento se supone que ha creado un proyecto de biblioteca de controles de formularios Windows Forms denominado WindowsFormsControlLibrary1, según el procedimiento descrito en [Cómo: crear el control](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)de usuario y host en un cuadro de diálogo .

### <a name="to-create-the-mfc-host-application"></a>Para crear la aplicación host MFC

1. Cree un proyecto de aplicación MFC.

   En el menú **Archivo** , seleccione **Nuevo**y, a continuación, haga clic en **Proyecto**. En la carpeta **Visual C++,** seleccione **Aplicación MFC**.

   En **Name** el cuadro `MFC02` Nombre , escriba y cambie la configuración **de solución** a **Agregar a solución**. Haga clic en **OK**.

   En el **Asistente para aplicaciones MFC**, acepte todos los valores predeterminados y, a continuación, haga clic en **Finalizar**. Esto crea una aplicación MFC con una interfaz de múltiples documentos.

1. Configure el proyecto para la compatibilidad con Common Language Runtime (CLR).

   En el **Explorador**de `MFC01` soluciones , haga clic con el botón secundario en el nodo del proyecto y seleccione **Propiedades** en el menú contextual. Aparece el cuadro de diálogo **Páginas** de propiedades.

   En **Propiedades de configuración**, seleccione **General**. En la sección **Valores predeterminados** del proyecto, establezca **Compatibilidad con Common Language Runtime en** Compatibilidad con Common Language Runtime **(/clr)**.

   En **Propiedades de configuración**, expanda **C/C++** y haga clic en el nodo **General.** Establezca Formato de información de **depuración** en Base de datos de programa **(/Zi).**

   Haga clic en el nodo **Generación de código.** Establezca **Habilitar reconstrucción mínima** en No **(/Gm-)**. Establezca también Comprobaciones de tiempo de **ejecución básicas en** **Predeterminado**.

   Haga clic en **Aceptar** para aplicar los cambios.

1. En *pch.h* (*stdafx.h* en Visual Studio 2017 y versiones anteriores), agregue la siguiente línea:

    ```
    #using <System.Windows.Forms.dll>
    ```

1. Agregue una referencia al control .NET.

   En **el Explorador**de `MFC02` soluciones , haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar**, **Referencias**. En la **página**de propiedades , haga clic en **Agregar nueva referencia**, seleccione WindowsFormsControlLibrary1 (en la pestaña **Proyectos)** y haga clic en **Aceptar**. Esto agrega una referencia en forma de una opción del compilador [/FU](../build/reference/fu-name-forced-hash-using-file.md) para que el programa se compile; también copia WindowsFormsControlLibrary1.dll `MFC02` en el directorio del proyecto para que se ejecute el programa.

1. En stdafx.h, encuentre esta línea:

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   Agregue estas líneas sobre ella:

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. Modifique la clase de vista para que herede de [CWinFormsView](../mfc/reference/cwinformsview-class.md).

   En MFC02View.h, reemplace [CView](../mfc/reference/cview-class.md) por [CWinFormsView](../mfc/reference/cwinformsview-class.md) para que el código aparezca de la siguiente manera:

    ```
    class CMFC02View : public CWinFormsView
    {
    };
    ```

   Si desea agregar vistas adicionales a la aplicación MDI, deberá llamar a [CWinApp::AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) para cada vista que cree.

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

1. Compile y ejecute el proyecto.

   En **el Explorador**de soluciones , haga clic con el botón secundario en MFC02 y seleccione Establecer como proyecto de **inicio**.

   En el menú **Compilar**, haga clic en **Compilar solución**.

   En el menú **Depurar** , haga clic en **Iniciar sin depurar**.

## <a name="see-also"></a>Consulte también

[Hospedar un control de usuario de Windows Forms como una vista de MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
