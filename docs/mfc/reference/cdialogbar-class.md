---
title: "CDialogBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDialogBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDialogBar class"
  - "dialog bars, Windows modeless dialog box"
  - "cuadros de diálogo, no modales"
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CDialogBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad de un cuadro de diálogo no modal de Windows en una barra de controles.  
  
## Sintaxis  
  
```  
class CDialogBar : public CControlBar  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDialogBar::CDialogBar](../Topic/CDialogBar::CDialogBar.md)|Crea un objeto `CDialogBar`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDialogBar::Create](../Topic/CDialogBar::Create.md)|Crea una barra de cuadro diálogo de Windows y la asocia al objeto de `CDialogBar` .|  
  
## Comentarios  
 Una barra de cuadro diálogo se parece a un cuadro de diálogo en que contiene los controles estándar de Windows entre los que puede el usuario pestaña.  Otra similitud es que crea una plantilla de cuadro de diálogo para representar la barra de cuadro de diálogo.  
  
 Crear y utilizar una barra de cuadro de diálogo es similar a crear y usar un objeto de `CFormView` .  Primero, utilice [editor de cuadros de diálogo](../../mfc/dialog-editor.md) para definir una plantilla de cuadro de diálogo con el estilo **WS\_CHILD** y ningún otro estilo.  la plantilla no debe tener el estilo **WS\_VISIBLE**.  En el código de aplicación, llame al constructor para crear el objeto de `CDialogBar` , llame a **Crear** para crear la ventana de la barra de cuadro de diálogo y para adjuntarla al objeto de `CDialogBar` .  
  
 Para obtener más información sobre `CDialogBar`, vea el artículo [Barras de cuadro de diálogo](../../mfc/dialog-bars.md) y [nota técnica 31](../../mfc/tn031-control-bars.md), barras de controles.  
  
> [!NOTE]
>  En la versión actual, un objeto de `CDialogBar` no puede hospedar controles de formularios Windows Forms.  Para obtener más información sobre los controles de formularios Windows Forms en Visual C\+\+, vea [Utilizar un control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CDialogBar`  
  
## Requisitos  
 **encabezado:** afxext.h  
  
## Vea también  
 [ejemplo CTRLBARS de MFC](../../top/visual-cpp-samples.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFormView Class](../../mfc/reference/cformview-class.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)