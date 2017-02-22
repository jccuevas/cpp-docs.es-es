---
title: "CMFCKeyMapDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCKeyMapDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCKeyMapDialog class"
ms.assetid: 5feb4942-d636-462d-a162-0104dd320f4e
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CMFCKeyMapDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCKeyMapDialog` admite un control que asigna los comandos a las claves del teclado.  
  
## Sintaxis  
  
```  
class CMFCKeyMapDialog : public CDialogEx  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCKeyMapDialog::CMFCKeyMapDialog](../Topic/CMFCKeyMapDialog::CMFCKeyMapDialog.md)|Crea un objeto `CMFCKeyMapDialog`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCKeyMapDialog::DoModal](../Topic/CMFCKeyMapDialog::DoModal.md)|Muestra un cuadro de diálogo de asignación de teclado.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCKeyMapDialog::FormatItem](../Topic/CMFCKeyMapDialog::FormatItem.md)|Llamado por el marco para compilar una cadena que describe una asignación de clave.  De forma predeterminada, la cadena contiene el nombre de comando, teclas de método abreviado utilizadas, y la descripción de la tecla de método abreviado.|  
|[CMFCKeyMapDialog::GetCommandKeys](../Topic/CMFCKeyMapDialog::GetCommandKeys.md)|Recupera una cadena que contiene una lista de las teclas de método abreviado asociadas al comando especificado.|  
|[CMFCKeyMapDialog::OnInsertItem](../Topic/CMFCKeyMapDialog::OnInsertItem.md)|Llamado por el marco antes de que un nuevo elemento se inserte en el control de lista interno que admite el control de asignación de teclado.|  
|[CMFCKeyMapDialog::OnPrintHeader](../Topic/CMFCKeyMapDialog::OnPrintHeader.md)|Llamado por el marco para imprimir el encabezado para la asignación de teclado en una nueva página.|  
|[CMFCKeyMapDialog::OnPrintItem](../Topic/CMFCKeyMapDialog::OnPrintItem.md)|Llamado por el marco para imprimir un elemento de asignación de teclado.|  
|[CMFCKeyMapDialog::OnSetColumns](../Topic/CMFCKeyMapDialog::OnSetColumns.md)|Llamado por el marco para establecer las leyendas para las columnas del control interno de la lista que admite el control de asignación de teclado.|  
|[CMFCKeyMapDialog::PrintKeyMap](../Topic/CMFCKeyMapDialog::PrintKeyMap.md)|Llamado por el marco cuando un usuario hace clic en el botón de **Impresión** .|  
|[CMFCKeyMapDialog::SetColumnsWidth](../Topic/CMFCKeyMapDialog::SetColumnsWidth.md)|Llamado por el marco para establecer el ancho de las columnas en el control de lista interno que admite el control de asignación de teclado.|  
  
## Comentarios  
 Utilice la clase de `CMFCKeyMapDialog` para implementar un cuadro de diálogo de asignación de teclado.  El cuadro de diálogo usa un control de vista de lista para mostrar los métodos abreviados de teclado y los comandos asociados.  
  
 Use la clase de `CMFCKeyMapDialog` en una aplicación, pase un puntero a la ventana de marco principal como parámetro al constructor de `CMFCKeyMapDialog` .  Llamar a continuación al método de `DoModal` para iniciar un cuadro de diálogo modal.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)  
  
## Requisitos  
 **encabezado:** afxkeymapdialog.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CKeyboardManager Class](../../mfc/reference/ckeyboardmanager-class.md)