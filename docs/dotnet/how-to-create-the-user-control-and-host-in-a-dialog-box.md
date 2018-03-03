---
title: "Cómo: crear el Control de usuario y el Host en un cuadro de diálogo | Documentos de Microsoft"
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
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: 03a53032-2f03-4fa2-b567-031615a26011
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 81a618c46f08366b9de2a02cbf84f73d42e7b108
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-the-user-control-and-host-in-a-dialog-box"></a>Cómo: Crear el control de usuario y el host en un cuadro de diálogo
Los pasos descritos en este artículo se supone que va a crear un objeto basado en el cuadro de diálogo ([CDialog (clase)](../mfc/reference/cdialog-class.md)) proyecto Microsoft Foundation Classes (MFC), pero también puede agregar compatibilidad para un control de formularios Windows Forms a un cuadro de diálogo MFC existente.  
  
### <a name="to-create-the-net-user-control"></a>Para crear el control de usuario de .NET  
  
1.  Cree un proyecto de Visual C# Control biblioteca de Windows Forms denominado `WindowsFormsControlLibrary1`.  
  
     En el menú **Archivo** , haga clic en **Nuevo** y, a continuación, haga clic en **Proyecto**. En el **Visual C#** carpeta, seleccione **biblioteca de controles de Windows Forms**.  
  
     Acepte la `WindowsFormsControlLibrary1` nombre del proyecto, haga clic en **Aceptar**.  
  
     De forma predeterminada, el nombre del control de .NET será `UserControl1`.  
  
2.  Agregar controles secundarios a `UserControl1`.  
  
     En el **cuadro de herramientas**, abra el **todos los formularios Windows Forms** lista. Arrastre un **botón** el control a la `UserControl1` superficie de diseño.  
  
     Agregar un **TextBox** control.  
  
3.  En **el Explorador de soluciones**, haga doble clic en **UserControl1.Designer.cs** para abrirlo y editarlo. Cambiar las declaraciones de cuadro de texto y el botón de `private` a `public`.  
  
4.  Compile el proyecto.  
  
     En el menú **Compilar** , haga clic en **Compilar solución**.  
  
### <a name="to-create-the-mfc-host-application"></a>Para crear la aplicación host MFC  
  
1.  Cree un proyecto de aplicación MFC.  
  
     En el menú **Archivo** , haga clic en **Nuevo** y, a continuación, haga clic en **Proyecto**. En el **Visual C++** carpeta, seleccione **aplicación MFC**.  
  
     En el cuadro **Nombre**, escriba `MFC01`. Cambiar la configuración de soluciones para **agregar a solución**. Haga clic en **Aceptar**.  
  
     En el **Asistente para aplicaciones MFC**, para el tipo de aplicación, seleccione **diálogo según**. Acepte los valores predeterminados restantes y haga clic en **finalizar**. Esto crea una aplicación MFC que tiene un cuadro de diálogo MFC.  
  
2.  Agregar un control de marcador de posición para el cuadro de diálogo MFC.  
  
     En el **vista** menú, haga clic en **vista de recursos**. En **vista de recursos**, expanda la **diálogo** carpeta y haga doble clic en `IDD_MFC01_DIALOG`. El recurso de cuadro de diálogo aparece en **Editor de recursos**.  
  
     En el **cuadro de herramientas**, abra el **Editor de cuadro de diálogo** lista. Arrastre un **texto estático** control para el recurso de cuadro de diálogo. El **texto estático** control actuará como un marcador de posición para el control de formularios Windows Forms. NET. Cambiar su tamaño aproximadamente al tamaño del control de formularios Windows Forms.  
  
     En el **propiedades** ventana, cambiar la **Id. de** de la **texto estático** el control a `IDC_CTRL1` y cambiar la **TabStop** propiedad **True**.  
  
3.  Configure el proyecto para la compatibilidad con Common Language Runtime (CLR).  
  
     En **el Explorador de soluciones**, haga clic en el nodo del proyecto MFC01 y, a continuación, haga clic en **propiedades**.  
  
     En el **páginas de propiedades** cuadro de diálogo **propiedades de configuración**, seleccione **General**. En el **valores predeterminados del proyecto** sección, establezca **compatible con Common Language Runtime** a **compatible con Common Language Runtime (/ clr)**.  
  
     En **propiedades de configuración**, expanda **C/C++** y seleccione la **General** nodo. Establecer **formato de la información de depuración** a **(/Zi) de la base de datos de programa**.  
  
     Seleccione el **generación de código** nodo. Establecer **habilitar recompilación mínima** a **No (/ Gm-)**. Establecer **comprobaciones en tiempo de ejecución básicas** a **predeterminado**.  
  
     Haga clic en **Aceptar** para aplicar los cambios.  
  
4.  Agregue una referencia al control .NET.  
  
     En **el Explorador de soluciones**, haga clic en el nodo del proyecto MFC01 y, a continuación, haga clic en **agregar**, **referencias**. En el **página de propiedades**, haga clic en **agregar nueva referencia**, seleccione **WindowsFormsControlLibrary1** (bajo la **proyectos** ficha) y haga clic en **Aceptar**. Esto agrega una referencia en forma de un [/FU](../build/reference/fu-name-forced-hash-using-file.md) opción del compilador para que el programa se compile. También coloca una copia del Windowsformscontrollibrary1 en la carpeta de proyecto \MFC01\ para que el programa se ejecutará.  
  
5.  En Stdafx.h, encuentre esta línea:  
  
    ```  
    #endif // _AFX_NO_AFXCMN_SUPPORT   
    ```  
  
     Por encima de él, agregue estas líneas:  
  
    ```  
    #include <afxwinforms.h>   // MFC Windows Forms support  
    ```  
  
6.  Agregue código para crear el control administrado.  
  
     En primer lugar, declare el control administrado. En MFC01Dlg.h, vaya a la declaración de la clase de cuadro de diálogo y agregar a un miembro de datos para el control de usuario en el ámbito protegido, como se indica a continuación.  
  
    ```  
    class CMFC01Dlg : public CDialog  
    {  
       // ...  
       // Data member for the .NET User Control:  
       CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_ctrl1;  
    ```  
  
     A continuación, proporcionar una implementación para el control administrado. En MFC01Dlg.cpp, en el cuadro de diálogo Reemplazar de `CMFC01Dlg::DoDataExchange` que se ha generado el Asistente para aplicaciones MFC (no `CAboutDlg::DoDataExchange`, que está en el mismo archivo), agregue el código siguiente para crear el control administrado y asociarlo con el marcador de posición estático IDC_CTRL1.  
  
    ```  
    void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)  
    {  
       CDialog::DoDataExchange(pDX);  
       DDX_ManagedControl(pDX, IDC_CTRL1, m_ctrl1);  
    }  
    ```  
  
7.  Compile y ejecute el proyecto.  
  
     En **el Explorador de soluciones**, haga clic en **MFC01** y, a continuación, haga clic en **establecer como proyecto de inicio**.  
  
     En el menú **Compilar** , haga clic en **Compilar solución**.  
  
     En el **depurar** menú, haga clic en **iniciar sin depurar**. El cuadro de diálogo MFC debe mostrar el control de formularios Windows Forms.  
  
## <a name="see-also"></a>Vea también  
 [Hospedar un control de usuario de Windows Forms en un cuadro de diálogo MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)