---
title: 'Cómo: Agregar enrutamientos de comandos al control de Windows Forms'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- command routing [C++], adding to Windows Forms controls
- Windows Forms controls [C++], command routing
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
ms.openlocfilehash: ad64a12051c22a0cfca99d3ec9c5abef579902f4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365170"
---
# <a name="how-to-add-command-routing-to-the-windows-forms-control"></a>Cómo: Agregar enrutamientos de comandos al control de Windows Forms

[CWinFormsView](../mfc/reference/cwinformsview-class.md) enruta comandos y mensajes de interfaz de usuario de comandos de actualización al control de usuario para permitirle controlar comandos MFC (por ejemplo, elementos de menú de marco y botones de barra de herramientas).

El control de usuario utiliza [ICommandTarget::Initialize](../mfc/reference/icommandtarget-interface.md#initialize) para almacenar `m_CmdSrc`una referencia al objeto de origen de comandos en , como se muestra en el ejemplo siguiente. Para usar `ICommandTarget`, debe agregar una referencia a mfcmifc80.dll.

`CWinFormsView` controla algunas de las notificaciones de vistas de MFC habituales reenviándolas al control del usuario administrado. Estas notificaciones incluyen los métodos [OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate), [OnUpdate](../mfc/reference/iview-interface.md#onupdate) y [OnActivateView](../mfc/reference/iview-interface.md#onactivateview) .

En este tema se supone que ha completado previamente [Cómo: Crear el control](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) de usuario y el host en un cuadro de diálogo y [Cómo: crear el control](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)de usuario y la vista MDI de host .

### <a name="to-create-the-mfc-host-application"></a>Para crear la aplicación host MFC

1. Abra la biblioteca de controles de formularios Windows Forms que creó en [Cómo: crear el control](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)de usuario y host en un cuadro de diálogo .

1. Agregue una referencia a mfcmifc80.dll, que puede hacer haciendo clic con el botón secundario en el nodo del proyecto en el **Explorador**de soluciones , seleccionando **Agregar**, **Referencia**y, a continuación, vaya a Microsoft Visual Studio 10.0-VC-atlmfc-lib.

1. Abra UserControl1.Designer.cs y agregue la instrucción using siguiente:

    ```
    using Microsoft.VisualC.MFC;
    ```

1. Además, en UserControl1.Designer.cs, cambie esta línea:

    ```
    partial class UserControl1
    ```

   a esto:

    ```
    partial class UserControl1 : System.Windows.Forms.UserControl, ICommandTarget
    ```

1. Agregue ésta como primera línea de la definición de clase para `UserControl1`:

    ```
    private ICommandSource m_CmdSrc;
    ```

1. Agregue las definiciones de método siguientes a `UserControl1` (crearemos el identificador del control MFC en el paso siguiente):

    ```
    public void Initialize (ICommandSource cmdSrc)
    {
       m_CmdSrc = cmdSrc;
       // need ID of control in MFC dialog and callback function
       m_CmdSrc.AddCommandHandler(32771, new CommandHandler (singleMenuHandler));
    }

    private void singleMenuHandler (uint cmdUI)
    {
       // User command handler code
       System.Windows.Forms.MessageBox.Show("Custom menu option was clicked.");
    }
    ```

1. Abra la aplicación MFC que creó en Cómo: Crear el control de [usuario y la vista MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)de host .

1. Agregue una opción de menú que llamará a `singleMenuHandler`.

   Vaya a **Vista** de recursos (Ctrl+Mayús+E), expanda la carpeta **Menú** y, a continuación, haga doble clic en **IDR_MFC02TYPE**. Se muestra el editor de menús.

   Agregue una opción de menú en la parte inferior del menú **Ver.** Observe el identificador de la opción de menú en la ventana **Propiedades.** Guarde el archivo.

   En el **Explorador**de soluciones , abra el archivo Resource.h, copie el valor de identificador `m_CmdSrc.AddCommandHandler` de la opción de `Initialize` menú que `32771` acaba de agregar y pegue ese valor como el primer parámetro en la llamada en el método del proyecto de C - (reemplazando si es necesario).

1. Compile y ejecute el proyecto.

   En el menú **Compilar**, haga clic en **Compilar solución**.

   En el menú **Depurar** , haga clic en **Iniciar sin depurar**.

   Seleccione la opción de menú que ha agregado. Observe que se llama al método en .dll.

## <a name="see-also"></a>Consulte también

[Hospedar un control de usuario de Windows Forms como una vista de MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Interfaz ICommandSource](../mfc/reference/icommandsource-interface.md)<br/>
[Interfaz ICommandTarget](../mfc/reference/icommandtarget-interface.md)
