---
title: "C&#243;mo: Llamar a propiedades y m&#233;todos del control de formularios Windows Forms | Microsoft Docs"
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
  - "llamar a métodos, control de Windows Forms"
  - "llamar a propiedades"
  - "llamar a propiedades, control de Windows Forms"
  - "llamadas a métodos, Windows Forms"
  - "controles de formularios Windows Forms [C++], métodos"
  - "controles de formularios Windows Forms [C++], propiedades"
ms.assetid: 6e647d8a-fdaa-4aa1-b3fe-04f15cff8eb3
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Llamar a propiedades y m&#233;todos del control de formularios Windows Forms
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CWinFormsView::GetControl](../Topic/CWinFormsView::GetControl.md) devuelve un puntero a <xref:System.Windows.Forms.Control?displayProperty=fullName> y no un puntero a `WindowsControlLibrary1::UserControl1`, por lo que es recomendable agregar un miembro del tipo de control de usuario e inicializarlo en [IView::OnInitialUpdate](../Topic/IView::OnInitialUpdate.md).  Ahora puede llamar a métodos y propiedades utilizando `m_ViewControl`.  
  
 En este tema se supone que el usuario ha completado [Cómo: Crear el control de usuario y hospedarlo en un cuadro de diálogo](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) y [Cómo: Crear el control de usuario y hospedarlo en una vista MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).  
  
### Para crear la aplicación host MFC  
  
1.  Abra la aplicación MFC creada en [Cómo: Crear el control de usuario y hospedarlo en una vista MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).  
  
2.  Agregue la línea siguiente a la sección pública de reemplazos de la declaración de clase `CMFC02View` en MFC02View.h.  
  
     `gcroot<WindowsFormsControlLibrary1::UserControl1 ^> m_ViewControl;`  
  
3.  Agregue un reemplazo para OnInitialupdate.  
  
     Muestre la ventana **Propiedades** \(F4\).  En **Vista de clases** \(CTRL\+MAYÚS\+C\), seleccione la clase CMFC02View.  En la ventana **Propiedades**, seleccione el icono de Reemplazos.  Desplácese por la lista a OnInitialUpdate.  Haga clic en la lista desplegable y seleccione \<agregar\>.  En MF C02 View.cpp se aseguran de que el cuerpo de la función OnInitialUpdate es como sigue:  
  
    ```  
    CWinFormsView::OnInitialUpdate();  
    m_ViewControl = safe_cast<WindowsFormsControlLibrary1::UserControl1 ^>(this->GetControl());  
    m_ViewControl->textBox1->Text = gcnew System::String("hi");  
    ```  
  
4.  Compile y ejecute el proyecto.  
  
     En el menú **Compilar**, haga clic en **Compilar solución**.  
  
     En el menú **Depurar**, haga clic en **Iniciar sin depurar**.  
  
     Observe que se ha inicializado el cuadro de texto.  
  
## Vea también  
 [Hospedar un control de usuario de Windows Forms como vista de MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)