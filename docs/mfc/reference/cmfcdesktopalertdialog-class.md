---
title: "CMFCDesktopAlertDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCDesktopAlertDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDesktopAlertDialog class"
ms.assetid: a53c60aa-9607-485b-b826-ec64962075f6
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CMFCDesktopAlertDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase `CMFCDesktopAlertDialog` se usa junto con la [CMFCDesktopAlertWnd Class](../../mfc/reference/cmfcdesktopalertwnd-class.md) para mostrar un cuadro de diálogo personalizado en una ventana emergente.  
  
## Sintaxis  
  
```  
class CMFCDesktopAlertDialog : public CDialogEx  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCDesktopAlertDialog::CreateFromParams](../Topic/CMFCDesktopAlertDialog::CreateFromParams.md)||  
|[CMFCDesktopAlertDialog::GetDlgSize](../Topic/CMFCDesktopAlertDialog::GetDlgSize.md)||  
|[CMFCDesktopAlertDialog::HasFocus](../Topic/CMFCDesktopAlertDialog::HasFocus.md)||  
|[CMFCDesktopAlertDialog::PreTranslateMessage](../Topic/CMFCDesktopAlertDialog::PreTranslateMessage.md)|\(Invalida `CDialogEx::PreTranslateMessage`\).|  
  
### Comentarios  
 Lleve a cabo los pasos siguientes para mostrar un cuadro de diálogo personalizado en una ventana emergente:  
  
1.  Derivar una clase de `CMFCDesktopAlertDialog`.  
  
2.  Crear una plantilla de cuadro de diálogo secundario en los recursos del proyecto.  
  
3.  Llamar a [CMFCDesktopAlertWnd::Create](../Topic/CMFCDesktopAlertWnd::Create.md) con el identificador de recurso de la plantilla de cuadro de diálogo y un puntero a la información en tiempo de ejecución de la clase derivada como parámetros.  
  
4.  Programar el cuadro de diálogo personalizado para tratar todas las notificaciones que proceden de los controles hospedados o programar los controles hospedados para tratar directamente estas notificaciones.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)  
  
## Requisitos  
 **Encabezado:** afxDesktopAlertDialog.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertWnd Class](../../mfc/reference/cmfcdesktopalertwnd-class.md)   
 [CMFCDesktopAlertWndInfo Class](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)   
 [CDialogEx Class](../../mfc/reference/cdialogex-class.md)