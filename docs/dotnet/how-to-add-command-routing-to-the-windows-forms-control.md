---
title: "Cómo: agregar comandos enrutamiento a Windows Forms Control | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- command routing [C++], adding to Windows Forms controls
- Windows Forms controls [C++], command routing
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bcd082b22c61e2444d70d936c225e538c2429222
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-add-command-routing-to-the-windows-forms-control"></a>Cómo: Agregar enrutamientos de comandos al control de Windows Forms
[CWinFormsView](../mfc/reference/cwinformsview-class.md) enruta los comandos y mensajes de interfaz de usuario de comando de actualización para el control de usuario para que pueda controlar los comandos MFC (por ejemplo, elementos de menú de marco y botones de barra de herramientas).  
  
 El control de usuario utiliza [ICommandTarget:: Initialize](../mfc/reference/icommandtarget-interface.md#initialize) para almacenar una referencia al objeto de origen de comando en `m_CmdSrc`, como se muestra en el ejemplo siguiente. Para usar `ICommandTarget`, debe agregar una referencia a mfcmifc80.dll.  
  
 `CWinFormsView` controla algunas de las notificaciones de vistas de MFC habituales reenviándolas al control del usuario administrado. Estas notificaciones incluyen el [OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate), [OnUpdate](../mfc/reference/iview-interface.md#onupdate) y [OnActivateView](../mfc/reference/iview-interface.md#onactivateview) métodos.  
  
 En este tema se da por supuesto que ha completado previamente [Cómo: crear el Control de usuario y el Host en un cuadro de diálogo](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) y [Cómo: crear el Control de usuario y el Host en una vista MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).  
  
### <a name="to-create-the-mfc-host-application"></a>Para crear la aplicación host MFC  
  
1.  Abra la biblioteca de controles de Windows Forms que creó en [Cómo: crear el Control de usuario y el Host en un cuadro de diálogo](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).  
  
2.  Agregue una referencia a mfcmifc80.dll, lo que puede hacer con el botón secundario en el nodo del proyecto **el Explorador de soluciones**, seleccione **agregar**, **referencia**y, a continuación, vaya a Microsoft Visual Studio 10.0\VC\atlmfc\lib.  
  
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
  
7.  Abra la aplicación MFC que creó en [Cómo: crear el Control de usuario y el Host en una vista MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).  
  
8.  Agregue una opción de menú que llamará a `singleMenuHandler`.  
  
     Vaya a **vista de recursos** (Ctrl + Mayús + E), expanda el **menú** carpeta y, a continuación, haga doble clic en **IDR_MFC02TYPE**. Se muestra el editor de menús.  
  
     Agregar una opción de menú en la parte inferior de la **vista** menú. Tenga en cuenta el identificador de la opción de menú en el **propiedades** ventana. Guarde el archivo.  
  
     En **el Explorador de soluciones**, abra el archivo Resource.h, copie el valor de identificador para la opción de menú que acaba de agregar y pegue ese valor como primer parámetro a la `m_CmdSrc.AddCommandHandler` llamar en el proyecto de C# `Initialize` método (reemplazando `32771` si es necesario).  
  
9. Compile y ejecute el proyecto.  
  
     En el menú **Compilar** , haga clic en **Compilar solución**.  
  
     En el **depurar** menú, haga clic en **iniciar sin depurar**.  
  
     Seleccione la opción de menú que ha agregado. Observe que se llama al método en .dll.  
  
## <a name="see-also"></a>Vea también  
 [Hospedar un Control de usuario de Windows Forms como vista MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)   
 [Interfaz ICommandSource](../mfc/reference/icommandsource-interface.md)   
 [Interfaz ICommandTarget](../mfc/reference/icommandtarget-interface.md)   
 [CommandHandler](http://msdn.microsoft.com/Library/22096734-e074-4aca-8523-4b15590109f9)