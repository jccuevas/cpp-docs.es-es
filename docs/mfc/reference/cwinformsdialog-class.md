---
title: "CWinFormsDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWinFormsDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinFormsDialog class"
  - "MFC [C++], compatibilidad con formularios Windows Forms"
  - "formularios Windows Forms [C++], compatibilidad con MFC"
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CWinFormsDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un contenedor para una clase de cuadro de diálogo MFC que hospeda un control de usuario de formularios Windows Forms.  
  
## Sintaxis  
  
```  
template <typename TManagedControl>  
class CWinFormsDialog :   
   public CDialog  
```  
  
#### Parámetros  
 `TManagedControl`  
 el control de usuario de .NET Framework que se mostrará en la aplicación MFC.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinFormsDialog::CWinFormsDialog](../Topic/CWinFormsDialog::CWinFormsDialog.md)|Crea un objeto `CWinFormsDialog`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinFormsDialog::GetControl](../Topic/CWinFormsDialog::GetControl.md)|Recupera una referencia al control de usuario de formularios Windows Forms.|  
|[CWinFormsDialog::GetControlHandle](../Topic/CWinFormsDialog::GetControlHandle.md)|Recupera un identificador de ventana al control de usuario de formularios Windows Forms.|  
|[CWinFormsDialog::OnInitDialog](../Topic/CWinFormsDialog::OnInitDialog.md)|Inicializa el cuadro de diálogo MFC creando y hospedar un control de usuario de formularios Windows Forms en él.|  
  
### Operadores públicos  
  
|Name||  
|----------|-|  
|[CWinFormsDialog::operator \-\>](../Topic/CWinFormsDialog::operator%20-%3E.md)|reemplaza [CWinFormsDialog::GetControl](../Topic/CWinFormsDialog::GetControl.md) en expresiones.|  
|[CWinFormsDialog::operator TManagedControl^](../Topic/CWinFormsDialog::operator%20TManagedControl%5E.md)|Convierte un tipo como una referencia a un control de usuario de formularios Windows Forms.|  
  
## Comentarios  
 `CWinFormsDialog` es un contenedor para una clase de cuadro de diálogo MFC \([CDialog](../../mfc/reference/cdialog-class.md)\) que hospeda un control de usuario de Windows Forms \(<xref:System.Windows.Forms.UserControl>\).  Esto permite la presentación de los controles de .NET Framework en un cuadro de diálogo de MFC modal o no modal.  
  
 Para obtener más información sobre cómo utilizar los formularios Windows Forms, vea [Utilizar un control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) y [Hospedar un control de usuario de Windows Forms en un cuadro de diálogo MFC](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md).  
  
## Requisitos  
 **encabezado:** afxwinforms.h  
  
## Vea también  
 <xref:System.Windows.Forms.UserControl?displayProperty=fullName>   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [CWinFormsView Class](../../mfc/reference/cwinformsview-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)