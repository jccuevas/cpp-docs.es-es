---
title: "Cómo: crear el Control de usuario y hospedarlo en una vista MDI | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 298a08689d6c4aa69d4a52af5fad965e3e353b5c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>Cómo: Crear el control de usuario y hospedarlo en una vista MDI
Los pasos siguientes muestran cómo crear un control de usuario de .NET Framework, editarlo en una biblioteca de clases de control (específicamente un proyecto de la Biblioteca de controles de Windows) y, después, compilar el proyecto en un ensamblado. Puede usar el control de una aplicación MFC que utiliza clases derivadas de [CView (clase)](../mfc/reference/cview-class.md) y [CWinFormsView Class](../mfc/reference/cwinformsview-class.md).  
  
 Para obtener información acerca de cómo crear un control de usuario de formularios Windows Forms y crear una biblioteca de clases de control, vea [Cómo: crear controles de usuario](/dotnet/framework/winforms/controls/how-to-author-composite-controls).  
  
> [!NOTE]
>  En algunos casos, puede que los controles de Windows Forms (por ejemplo, un control Grid de un tercero) no se comporten de forma confiable si se hospedan en una aplicación MFC. La solución recomendada es colocar un control de usuario de formularios Windows Forms en la aplicación MFC y el control Grid de un tercero dentro del control de usuario.  
  
 Este procedimiento se supone que ha creado un proyecto de biblioteca de controles de Windows Forms denominado WindowsFormsControlLibrary1, según el procedimiento de [Cómo: crear el Control de usuario y el Host en un cuadro de diálogo](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).  
  
### <a name="to-create-the-mfc-host-application"></a>Para crear la aplicación host MFC  
  
1.  Cree un proyecto de aplicación MFC.  
  
     En el **archivo** menú, seleccione **New**y, a continuación, haga clic en **proyecto**. En el **Visual C++** carpeta, seleccione **aplicación MFC**.  
  
     En el **nombre** cuadro, escriba `MFC02` y cambie el **solución** si se establece en **agregar a solución**. Haga clic en **Aceptar**.  
  
     En el **Asistente para aplicaciones MFC**, acepte todos los valores predeterminados y, a continuación, haga clic en **finalizar**. Esto crea una aplicación MFC con una interfaz de múltiples documentos.  
  
2.  Configure el proyecto para la compatibilidad con Common Language Runtime (CLR).  
  
     En **el Explorador de soluciones**, haga clic en el `MFC01` nodo de proyecto y seleccione **propiedades** en el menú contextual. El **páginas de propiedades** aparece el cuadro de diálogo.  
  
     En **propiedades de configuración**, seleccione **General**. En el **valores predeterminados del proyecto** sección, establezca **compatible con Common Language Runtime** a **compatible con Common Language Runtime (/ clr)**.  
  
     En **propiedades de configuración**, expanda **C/C++** y haga clic en el **General** nodo. Establecer **formato de la información de depuración** a **(/Zi) de la base de datos de programa**.  
  
     Haga clic en el **generación de código** nodo. Establecer **habilitar recompilación mínima** a **No (/ Gm-)**. Establecer **comprobaciones en tiempo de ejecución básicas** a **predeterminado**.  
  
     Haga clic en **Aceptar** para aplicar los cambios.  
  
3.  En stdafx.h, agregue la línea siguiente:  
  
    ```  
    #using <System.Windows.Forms.dll>  
    ```  
  
4.  Agregue una referencia al control .NET.  
  
     En **el Explorador de soluciones**, haga clic en el `MFC02` nodo del proyecto y seleccione **agregar**, **referencias**. En el **página de propiedades**, haga clic en **agregar nueva referencia**, seleccione WindowsFormsControlLibrary1 (en la **proyectos** ficha) y haga clic en **Aceptar** . Esto agrega una referencia en forma de un [/FU](../build/reference/fu-name-forced-hash-using-file.md) opción del compilador para que el programa se compile; también se copiará Windowsformscontrollibrary1 en el `MFC02` directorio del proyecto para que el programa se ejecutará.  
  
5.  En stdafx.h, encuentre esta línea:  
  
    ```  
    #endif // _AFX_NO_AFXCMN_SUPPORT   
    ```  
  
     Agregue estas líneas sobre ella:  
  
    ```  
    #include <afxwinforms.h>   // MFC Windows Forms support  
    ```  
  
6.  Modificar la clase de vista para que herede de [CWinFormsView](../mfc/reference/cwinformsview-class.md).  
  
     En MFC02View.h, reemplace [CView](../mfc/reference/cview-class.md) con [CWinFormsView](../mfc/reference/cwinformsview-class.md) para que el código aparezca como sigue:  
  
    ```  
    class CMFC02View : public CWinFormsView  
    {  
    };  
    ```  
  
     Si desea agregar vistas adicionales a la aplicación MDI, deberá llamar a [CWinApp:: AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) para cada vista que cree.  
  
7.  Modifique el archivo MFC02View.cpp para cambiar CView a CWinFormsView en la macro IMPLEMENT_DYNCREATE y en el mapa de mensajes, y reemplace el constructor vacío existente por el constructor que se muestra a continuación:  
  
    ```  
    IMPLEMENT_DYNCREATE(CMFC02View, CWinFormsView)  
  
    CMFC02View::CMFC02View(): CWinFormsView(WindowsFormsControlLibrary1::UserControl1::typeid)   
    {  
    }  
    BEGIN_MESSAGE_MAP(CMFC02View, CWinFormsView)  
    //leave existing body as is  
    END_MESSAGE_MAP()  
    ```  
  
8.  Compile y ejecute el proyecto.  
  
     En **el Explorador de soluciones**, haga clic en MFC02 y seleccione **establecer como proyecto de inicio**.  
  
     En el menú **Compilar** , haga clic en **Compilar solución**.  
  
     En el **depurar** menú, haga clic en **iniciar sin depurar**.  
  
## <a name="see-also"></a>Vea también  
 [Hospedar un control de usuario de Windows Forms como una vista de MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)