---
title: "C&#243;mo: Crear el control de usuario y hospedarlo en una vista MDI | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC [C++], Controles de Windows Forms"
  - "formularios Windows Forms [C++], compatibilidad con MFC"
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Crear el control de usuario y hospedarlo en una vista MDI
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los pasos siguientes muestran cómo crear un control de usuario de .NET Framework, editarlo en una biblioteca de clases de control \(específicamente un proyecto de la Biblioteca de controles de Windows\) y, después, compilar el proyecto en un ensamblado.  A continuación, el control se podrá usar desde una aplicación MFC que utiliza clases derivadas de [CView Class](../mfc/reference/cview-class.md) y [CWinFormsView Class](../mfc/reference/cwinformsview-class.md).  
  
 Para obtener información sobre cómo crear un control de usuario de formularios Windows Forms y generar una biblioteca de clases de control, vea [Cómo: Crear controles de usuario](../Topic/How%20to:%20Author%20Composite%20Controls.md).  
  
> [!NOTE]
>  En algunos casos, puede que los controles de Windows Forms \(por ejemplo, un control Grid de un tercero\) no se comporten de forma confiable si se hospedan en una aplicación MFC.  La solución recomendada es colocar un control de usuario de formularios Windows Forms en la aplicación MFC y el control Grid de un tercero dentro del control de usuario.  
  
 En este procedimiento se presupone que se creó un proyecto de la Biblioteca de controles de Windows Forms denominado WindowsFormsControlLibrary1, según el procedimiento de [Cómo: Crear el control de usuario y hospedarlo en un cuadro de diálogo](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).  
  
### Para crear la aplicación host MFC  
  
1.  Cree un proyecto de aplicación MFC.  
  
     En el menú **Archivo**, seleccione **Nuevo** y, a continuación, haga clic en **Proyecto**.  En la carpeta **Visual C\+\+**, seleccione **Aplicación MFC**.  
  
     En el cuadro **Nombre**, escriba `MFC02` y cambie el valor **Solución** a **Agregar a solución**.  Haga clic en **Aceptar**.  
  
     En el **Asistente para aplicaciones MFC**, acepte todos los valores predeterminados y, a continuación, haga clic en **Finalizar**.  Esto crea una aplicación MFC con una interfaz de múltiples documentos.  
  
2.  Configure el proyecto para la compatibilidad con Common Language Runtime \(CLR\).  
  
     En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto `MFC01` y, a continuación, seleccione **Propiedades** en el menú contextual.  Aparecerá el cuadro de diálogo **Páginas de propiedades**.  
  
     En **Propiedades de configuración**, seleccione **General**.  En la sección **Valores predeterminados del proyecto**, establezca **Compatibilidad con Common Language Runtime** en **Compatible con Common Language Runtime \(\/clr\)**.  
  
     En **Propiedades de configuración**, expanda **C\/C\+\+** y haga clic en el nodo **General**.  Establezca **Formato de información de depuración** en **Base de datos de programa \(\/Zi\)**.  
  
     Haga clic en el nodo **Generación de código**.  Establezca **Habilitar recompilación mínima** en **No \(\/Gm\-\)**.  Establezca también **Comprobaciones básicas en tiempo de ejecución** en **Predeterminado**.  
  
     Haga clic en **Aceptar** para aplicar los cambios.  
  
3.  En stdafx.h, agregue la línea siguiente:  
  
    ```  
    #using <System.Windows.Forms.dll>  
    ```  
  
4.  Agregue una referencia al control .NET.  
  
     En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto `MFC02` y, a continuación, seleccione **Agregar**, **Referencias**.  En la **Página de propiedades**, haga clic en **Agregar nueva referencia**, seleccione WindowsFormsControlLibrary1 \(en la pestaña **Proyectos**\) y haga clic en **Aceptar**.  De este modo, se agregará una referencia en forma de opción del compilador [\/FU](../build/reference/fu-name-forced-hash-using-file.md) para que el programa se compile; también se copiará WindowsFormsControlLibrary1 en el directorio del proyecto `MFC02` para que se ejecute el programa.  
  
5.  En stdafx.h, encuentre esta línea:  
  
    ```  
    #endif // _AFX_NO_AFXCMN_SUPPORT   
    ```  
  
     Agregue estas líneas sobre ella:  
  
    ```  
    #include <afxwinforms.h>   // MFC Windows Forms support  
    ```  
  
6.  Modifique la clase de vista para que herede de [CWinFormsView](../mfc/reference/cwinformsview-class.md).  
  
     En MFC02View.h, reemplace [CView](../mfc/reference/cview-class.md) con [CWinFormsView](../mfc/reference/cwinformsview-class.md) para que el código aparezca como sigue:  
  
    ```  
    class CMFC02View : public CWinFormsView  
    {  
    };  
    ```  
  
     Si desea agregar vistas adicionales a su aplicación MDI, deberá llamar a [CWinApp::AddDocTemplate](../Topic/CWinApp::AddDocTemplate.md) para cada vista que cree.  
  
7.  Modifique el archivo MFC02View.cpp para cambiar CView a CWinFormsView en la macro IMPLEMENT\_DYNCREATE y en el mapa de mensajes, y reemplace el constructor vacío existente por el constructor que se muestra a continuación:  
  
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
  
     En el **Explorador de soluciones**, haga clic con el botón secundario en MFC02 y seleccione **Establecer como proyecto de inicio**.  
  
     En el menú **Compilar**, haga clic en **Compilar solución**.  
  
     En el menú **Depurar**, haga clic en **Iniciar sin depurar**.  
  
## Vea también  
 [Hospedar un control de usuario de Windows Forms como vista de MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)