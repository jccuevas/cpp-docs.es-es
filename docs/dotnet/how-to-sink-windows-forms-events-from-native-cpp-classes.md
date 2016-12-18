---
title: "C&#243;mo: Recibir eventos de Windows Forms de clases nativas de C++ | Microsoft Docs"
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
  - "control de eventos, Interoperabilidad nativa y de .NET"
  - "control de eventos, Interoperabilidad nativa y administrada"
  - "control de eventos, recibir .NET en C++"
  - "control de eventos, formularios Windows Forms en C++"
ms.assetid: 6e30ddee-d058-4c8d-9956-2a43d86f19d5
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Recibir eventos de Windows Forms de clases nativas de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se pueden habilitar clases C\+\+ nativas para recibir devoluciones de llamada desde eventos administrados elevados a partir de controles de formularios Windows Forms u otros formularios con formato de mapa de macros de MFC.  La recepción de eventos en vistas y cuadros de diálogo es similar a la misma tarea efectuada para los controles.  
  
 Para ello, debe:  
  
-   Adjuntar un controlador de eventos `OnClick` al control mediante [MAKE\_DELEGATE](../Topic/MAKE_DELEGATE.md).  
  
-   Crear un mapa de delegados mediante [BEGIN\_DELEGATE\_MAP](../Topic/BEGIN_DELEGATE_MAP.md), [END\_DELEGATE\_MAP](../Topic/END_DELEGATE_MAP.md) y [EVENT\_DELEGATE\_ENTRY](../Topic/EVENT_DELEGATE_ENTRY.md).  
  
 Este ejemplo continúa el trabajo realizado en [Cómo: Enlazar datos DDX\/DDV con formularios Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).  
  
 Ahora, asociará el control MFC \(`m_MyControl`\) a un delegado del controlador de eventos administrados denominado `OnClick` para el evento <xref:System.Windows.Forms.Control.Click> administrado.  
  
### Para adjuntar el controlador de eventos OnClick:  
  
1.  Agregue el código siguiente a la implementación de BOOL CMFC01Dlg::OnInitDialog:  
  
    ```  
    m_MyControl.GetControl()->button1->Click += MAKE_DELEGATE( System::EventHandler, OnClick );  
    ```  
  
2.  Agregue el código siguiente a la sección public de la declaración de la clase CMFC01Dlg : public CDialog.  
  
    ```  
    // delegate map  
    BEGIN_DELEGATE_MAP( CMFC01Dlg )  
    EVENT_DELEGATE_ENTRY( OnClick, System::Object^, System::EventArgs^ )  
    END_DELEGATE_MAP()  
  
    void OnClick( System::Object^ sender, System::EventArgs^ e );  
    ```  
  
3.  Finalmente, agregue la implementación de `OnClick` a CMFC01Dlg.cpp:  
  
    ```  
    void CMFC01Dlg::OnClick(System::Object^ sender, System::EventArgs^ e)  
    {  
        AfxMessageBox(_T("Button clicked"));  
    }  
    ```  
  
## Vea también  
 [MAKE\_DELEGATE](../Topic/MAKE_DELEGATE.md)   
 [BEGIN\_DELEGATE\_MAP](../Topic/BEGIN_DELEGATE_MAP.md)   
 [END\_DELEGATE\_MAP](../Topic/END_DELEGATE_MAP.md)   
 [EVENT\_DELEGATE\_ENTRY](../Topic/EVENT_DELEGATE_ENTRY.md)