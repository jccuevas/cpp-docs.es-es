---
title: "C&#243;mo: Crear el control de usuario y hospedarlo en un cuadro de di&#225;logo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "MFC [C++], alojar un control de formularios Windows Forms"
  - "formularios Windows Forms [C++], compatibilidad con MFC"
ms.assetid: 03a53032-2f03-4fa2-b567-031615a26011
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Crear el control de usuario y hospedarlo en un cuadro de di&#225;logo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En los pasos de este artículo se supone que va a crear un proyecto de Microsoft Foundation Classes \(MFC\) basado en cuadros de diálogo \([CDialog Class](../mfc/reference/cdialog-class.md)\), pero también puede agregar compatibilidad para un control de Windows Forms a un cuadro de diálogo MFC existente.  
  
### Para crear el control de usuario .NET  
  
1.  Cree un proyecto de biblioteca de controles de Windows Forms de Visual C\# denominado `WindowsFormsControlLibrary1`.  
  
     En el menú **Archivo**, haga clic en **Nuevo** y, a continuación, haga clic en **Proyecto**.  En la carpeta **Visual C\#**, seleccione **Biblioteca de controles de Windows Forms**.  
  
     Acepte el nombre del proyecto `WindowsFormsControlLibrary1` haciendo clic en **Aceptar**.  
  
     De forma predeterminada, el nombre del control de .NET será `UserControl1`.  
  
2.  Agregue los controles secundarios a `UserControl1`.  
  
     En el **Cuadro de herramientas**, abra la lista **Todos los formularios Windows Forms**.  Arrastre un control de botón hacia la superficie de diseño `UserControl1`.  
  
     Agregue también un control **TextBox**.  
  
3.  En el **Explorador de soluciones**, haga doble clic en **UserControl1.Designer.cs** a fin de abrirlo para su edición.  Cambie las declaraciones de TextBox y Button de `private` a `public`.  
  
4.  Compile el proyecto.  
  
     En el menú **Compilar**, haga clic en **Compilar solución**.  
  
### Para crear la aplicación host MFC  
  
1.  Cree un proyecto de aplicación MFC.  
  
     En el menú **Archivo**, haga clic en **Nuevo** y, a continuación, haga clic en **Proyecto**.  En la carpeta **Visual C\+\+**, seleccione **Aplicación MFC**.  
  
     En el cuadro **Nombre**, escriba `MFC01`.  Cambie la configuración de la solución a **Agregar a solución**.  Haga clic en **Aceptar**.  
  
     En el **Asistente para aplicaciones MFC**, para Tipo de aplicación, seleccione **Basado en cuadros de diálogo**.  Acepte los valores predeterminados restantes y haga clic en **Finalizar**.  Esto crea una aplicación MFC que tiene un cuadro de diálogo MFC.  
  
2.  Agregue un control de marcador de posición al cuadro de diálogo MFC.  
  
     Haga clic en **Vista de recursos** en el menú **Ver**.  En **Vista de recursos**, expanda la carpeta **Cuadro de diálogo** y haga doble clic en `IDD_MFC01_DIALOG`.  Aparecerá el recurso de cuadro de diálogo en el **Editor de recursos**.  
  
     En el **Cuadro de herramientas**, abra la lista **Editor de cuadros de diálogo**.  Arrastre un control de texto estático hacia el recurso de cuadro de diálogo.  El control **Static Text** actuará como un marcador de posición para el control de Windows Forms de .NET.  Cambie su tamaño aproximadamente al del tamaño del control de formularios Windows Forms.  
  
     En la ventana **Propiedades**, cambie el **identificador** del control **Static Text** a `IDC_CTRL1` y cambie la propiedad **TabStop** a **True**.  
  
3.  Configure el proyecto para la compatibilidad con Common Language Runtime \(CLR\).  
  
     En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto MFC01 y, a continuación, haga clic en **Propiedades**.  
  
     En el cuadro de diálogo **Páginas de propiedades**, en **Propiedades de configuración**, seleccione **General**.  En la sección **Valores predeterminados del proyecto**, establezca **Compatibilidad con Common Language Runtime** en **Compatible con Common Language Runtime \(\/clr\)**.  
  
     Bajo **Propiedades de configuración**, expanda **C\/C\+\+** y seleccione el nodo **General**.  Establezca **Formato de información de depuración** en **Base de datos de programa \(\/Zi\)**.  
  
     Seleccione el nodo **Generación de código**.  Establezca **Habilitar recompilación mínima** en **No \(\/Gm\-\)**.  Establezca también **Comprobaciones básicas en tiempo de ejecución** en **Predeterminado**.  
  
     Haga clic en **Aceptar** para aplicar los cambios.  
  
4.  Agregue una referencia al control .NET.  
  
     En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto MFC01 y, a continuación, haga clic en **Agregar**, **Referencias**.  En la **Página de propiedades**, haga clic en **Agregar nueva referencia**, seleccione **WindowsFormsControlLibrary1** \(bajo la pestaña **Proyectos**\) y haga clic en **Aceptar**.  Esto agrega una referencia en forma de opción de compilador [\/FU](../build/reference/fu-name-forced-hash-using-file.md) para que el programa se compile.  También coloca una copia de WindowsFormsControlLibrary1.dll en la carpeta de proyecto \\MFC01\\ para que el programa se ejecute.  
  
5.  En Stdafx.h, busque esta línea:  
  
    ```  
    #endif // _AFX_NO_AFXCMN_SUPPORT   
    ```  
  
     Agregue estas líneas sobre ella:  
  
    ```  
    #include <afxwinforms.h>   // MFC Windows Forms support  
    ```  
  
6.  Agregue el código para crear el control administrado.  
  
     Primero, declare el control administrado.  En MFC01Dlg.h, vaya a la declaración de la clase del cuadro de diálogo y agregue un miembro de datos para el control de usuario en el ámbito protegido del modo siguiente:  
  
    ```  
    class CMFC01Dlg : public CDialog  
    {  
       // ...  
       // Data member for the .NET User Control:  
       CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_ctrl1;  
    ```  
  
     Luego, proporcione una implementación para el control administrado.  En MFC01Dlg.cpp, en el reemplazo del cuadro de diálogo de `CMFC01Dlg::DoDataExchange` generado por el asistente para aplicaciones MFC \(y no `CAboutDlg::DoDataExchange`, que está en el mismo archivo\), agregue el código siguiente para crear el control administrado y asociarlo al marcador de posición estático IDC\_CTRL1.  
  
    ```  
    void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)  
    {  
       CDialog::DoDataExchange(pDX);  
       DDX_ManagedControl(pDX, IDC_CTRL1, m_ctrl1);  
    }  
    ```  
  
7.  Compile y ejecute el proyecto.  
  
     En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en **MFC01** y, a continuación, haga clic en **Establecer como proyecto de inicio**.  
  
     En el menú **Compilar**, haga clic en **Compilar solución**.  
  
     En el menú **Depurar**, haga clic en **Iniciar sin depurar**.  El cuadro de diálogo MFC debería mostrar el control de Windows Forms.  
  
## Vea también  
 [Hospedar un control de usuario de Windows Forms en un cuadro de diálogo MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)