---
title: "C&#243;mo: Agregar enrutamientos de comandos al control de Windows Forms | Microsoft Docs"
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
  - "enrutamiento de comandos [C++], agregar a controles de formularios Windows Forms"
  - "Enrutamiento de comandos de controles de formularios Windows Forms [C++]"
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# C&#243;mo: Agregar enrutamientos de comandos al control de Windows Forms
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CWinFormsView](../mfc/reference/cwinformsview-class.md) enruta los comandos y mensajes de interfaz de Usuario de comandos de actualización para el control de usuario para que pueda controlar los comandos MFC (por ejemplo, elementos de menú de marcos y botones de barra de herramientas).  
  
 El control de usuario utiliza [ICommandTarget:: Initialize](../Topic/ICommandTarget::Initialize.md) para almacenar una referencia al objeto de origen de comando en `m_CmdSrc`, como se muestra en el ejemplo siguiente. Para usar `ICommandTarget`, debe agregar una referencia a mfcmifc80.dll.  
  
 `CWinFormsView` controla algunas de las notificaciones de vistas de MFC habituales reenviándolas al control del usuario administrado. Estas notificaciones incluyen el [OnInitialUpdate](../Topic/IView::OnInitialUpdate.md), [OnUpdate](../Topic/IView::OnUpdate.md) y [OnActivateView](../Topic/IView::OnActivateView.md) métodos de la [interfaz IView](../mfc/reference/iview-interface.md).  
  
 Este tema se supone que ha completado [Cómo: crear el Control de usuario y hospedarlo en un cuadro de diálogo](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) y [Cómo: crear el Control de usuario y el Host en una vista MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).  
  
### <a name="to-create-the-mfc-host-application"></a>Para crear la aplicación host MFC  
  
1.  Abra la biblioteca de controles de Windows Forms que creó en [Cómo: crear el Control de usuario y hospedarlo en un cuadro de diálogo](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).  
  
2.  Agregue una referencia a mfcmifc80.dll, que se puede realizar haciendo clic en el nodo del proyecto en **el Explorador de soluciones**, seleccionar **Agregar**, **referencia**, y, a continuación, vaya a Microsoft Visual Studio 10.0\VC\atlmfc\lib.  
  
3.  Abra UserControl1.Designer.cs y agregue la instrucción using siguiente:  
  
    ```  
    using Microsoft.VisualC.MFC;  
    ```  
  
4.  Además, en UserControl1.Designer.cs, cambie esta línea:  
  
    ```  
    partial class UserControl1  
    ```  
  
     a:  
  
    ```  
    partial class UserControl1 : System.Windows.Forms.UserControl, ICommandTarget  
    ```  
  
5.  Agregue ésta como primera línea de la definición de clase para `UserControl1`:  
  
    ```  
    private ICommandSource m_CmdSrc;  
    ```  
  
6.  Agregue las definiciones de método siguientes a `UserControl1` (crearemos el identificador del control MFC en el paso siguiente):  
  
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
  
7.  Abra la aplicación MFC creada en [Cómo: crear el Control de usuario y el Host en una vista MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).  
  
8.  Agregue una opción de menú que llamará a `singleMenuHandler`.  
  
     Vaya a **vista de recursos** (Ctrl + Mayús + E), expanda el **menú** carpeta y, a continuación, haga doble clic en **IDR_MFC02TYPE**. Se muestra el editor de menús.  
  
     Agregar una opción de menú en la parte inferior de la **vista** menú. Observe el identificador de la opción de menú en la **propiedades** ventana. Guarde el archivo.  
  
     En **el Explorador de soluciones**, abra el archivo Resource.h, copie el valor de Id. de la opción de menú que acaba de agregar y pegue ese valor como primer parámetro para el `m_CmdSrc.AddCommandHandler` llamar en C# del proyecto `Initialize` (método) (reemplazando `32771` Si es necesario).  
  
9. Compile y ejecute el proyecto.  
  
     En el menú **Compilar** , haga clic en **Compilar solución**.  
  
     En el **Depurar** menú, haga clic en **Iniciar sin depurar**.  
  
     Seleccione la opción de menú que ha agregado. Observe que se llama al método en .dll.  
  
## <a name="see-also"></a>Vea también  
 [Hospedar un Control de usuario de Windows Forms como vista MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)   
 [Interfaz de ICommandSource](../mfc/reference/icommandsource-interface.md)   
 [Interfaz ICommandTarget](../mfc/reference/icommandtarget-interface.md)   
 [CommandHandler](../Topic/CommandHandler%20Delegate.md)