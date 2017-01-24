---
title: "CStatic Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CStatic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mapas de bits, mostrar"
  - "controles [MFC], static"
  - "CStatic class"
  - "cursores, mostrar"
  - "enhanced metafiles"
  - "enhanced metafiles, mostrar"
  - "iconos, mostrar"
  - "static controls"
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStatic Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

proporciona la funcionalidad de un control estático de Windows.  
  
## Sintaxis  
  
```  
class CStatic : public CWnd  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStatic::CStatic](../Topic/CStatic::CStatic.md)|Crea un objeto `CStatic`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStatic::Create](../Topic/CStatic::Create.md)|Crea el control estático de Windows y lo asocia al objeto de `CStatic` .|  
|[CStatic::DrawItem](../Topic/CStatic::DrawItem.md)|Reemplazo para dibujar un control estático dibujado por.|  
|[CStatic::GetBitmap](../Topic/CStatic::GetBitmap.md)|Recupera el identificador del mapa de bits establecido previamente con [SetBitmap](../Topic/CStatic::SetBitmap.md).|  
|[CStatic::GetCursor](../Topic/CStatic::GetCursor.md)|Recupera el identificador de la imagen del cursor establecido previamente con [SetCursor](../Topic/CStatic::SetCursor.md).|  
|[CStatic::GetEnhMetaFile](../Topic/CStatic::GetEnhMetaFile.md)|Recupera el identificador de metarchivo mejorado establecido previamente con [SetEnhMetaFile](../Topic/CStatic::SetEnhMetaFile.md).|  
|[CStatic::GetIcon](../Topic/CStatic::GetIcon.md)|Recupera el identificador del icono establecido previamente con [SetIcon](../Topic/CStatic::SetIcon.md).|  
|[CStatic::SetBitmap](../Topic/CStatic::SetBitmap.md)|especifica un mapa de bits que se mostrará en el control estático.|  
|[CStatic::SetCursor](../Topic/CStatic::SetCursor.md)|Especifica una imagen de cursor que se va a mostrar en el control estático.|  
|[CStatic::SetEnhMetaFile](../Topic/CStatic::SetEnhMetaFile.md)|Especifica un metarchivo mejorado que se mostrará en el control estático.|  
|[CStatic::SetIcon](../Topic/CStatic::SetIcon.md)|especifica un icono que se mostrará en el control estático.|  
  
## Comentarios  
 Un control estático muestra una cadena de texto, un cuadro, un rectángulo, un icono, el cursor, un mapa de bits, o un metarchivo mejorado.  Se puede utilizar para etiquetar, cuadro, o para separar otros controles.  un control estático no toma ninguna entrada y no proporciona normalmente ninguna salida; sin embargo, puede notificar a su elemento primario de clic del mouse si ha creado con el estilo de **SS\_NOTIFY** .  
  
 cree un control estático en dos pasos.  Primero, llame al constructor para crear el objeto de `CStatic` , llame a la función miembro de [Crear](../Topic/CStatic::Create.md) para crear el control estático y para adjuntarlo al objeto de `CStatic` .  
  
 Si crea un objeto de `CStatic` dentro de un cuadro de diálogo \(a través de un recurso de cuadro de diálogo\), el objeto de `CStatic` automáticamente se destruye cuando el usuario cierra el cuadro de diálogo.  
  
 Si crea un objeto de `CStatic` dentro de una ventana, puede necesitar también destruirla.  un objeto de `CStatic` creado en la pila dentro de una ventana automáticamente se destruye.  Si crea el objeto de `CStatic` en la pila mediante la función de **nuevo** , debe llamar a **cancelación** en el objeto para destruirlo cuando haya terminado con él.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatic`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [CButton Class](../../mfc/reference/cbutton-class.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)   
 [CScrollBar Class](../../mfc/reference/cscrollbar-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)