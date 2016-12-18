---
title: "CMFCToolBarFontComboBox Class | Microsoft Docs"
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
  - "CMFCToolBarFontComboBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarFontComboBox class"
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
caps.latest.revision: 29
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCToolBarFontComboBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un botón de la barra de herramientas que contiene un control de cuadro combinado que permite al usuario seleccionar una fuente en una lista de fuentes del sistema.  
  
## Sintaxis  
  
```  
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton  
```  
  
## Members  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](../Topic/CMFCToolBarFontComboBox::CMFCToolBarFontComboBox.md)|Crea un objeto `CMFCToolBarFontComboBox`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarFontComboBox::GetFontDesc](../Topic/CMFCToolBarFontComboBox::GetFontDesc.md)|Devuelve un puntero al objeto de `CMFCFontInfo` para un índice especificado en el cuadro combinado.|  
|[CMFCToolBarFontComboBox::SetFont](../Topic/CMFCToolBarFontComboBox::SetFont.md)|Selecciona una fuente en el cuadro combinado de la fuente del nombre de fuente, o el prefijo y el juego de caracteres de la fuente.|  
  
### miembros de datos  
 [CMFCToolBarFontComboBox::m\_nFontHeight](../Topic/CMFCToolBarFontComboBox::m_nFontHeight.md)  
 El alto de los caracteres del cuadro combinado de la fuente.  
  
## Comentarios  
 Para agregar un botón del cuadro combinado de la fuente a una barra de herramientas, siga estos pasos:  
  
1.  Reserva un Id. de recurso ficticio para el botón del recurso primario de la barra de herramientas.  
  
2.  Construya un objeto `CMFCToolBarFontComboBox`.  
  
3.  En el controlador de mensajes que procesa el mensaje de `AFX_WM_RESETTOOLBAR` , reemplace el botón original con el nuevo botón de cuadro combinado con [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md).  
  
4.  Sincronice la fuente seleccionada en el cuadro combinado con la del documento utilizando el método de [CMFCToolBarFontComboBox::SetFont](../Topic/CMFCToolBarFontComboBox::SetFont.md) .  
  
 Para sincronizar la fuente del documento con la fuente seleccionada en el cuadro combinado, use el método de [CMFCToolBarFontComboBox::GetFontDesc](../Topic/CMFCToolBarFontComboBox::GetFontDesc.md) para recuperar los atributos de la fuente seleccionada, y utilizar esos atributos para crear un objeto de [CFont Class](../../mfc/reference/cfont-class.md) .  
  
 El botón del cuadro combinado de la fuente llama a la función [EnumFontFamiliesEx](http://msdn.microsoft.com/library/windows/desktop/dd162620) Win32 para determinar las fuentes de pantalla y de impresora disponible en el sistema.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)  
  
## Requisitos  
 **encabezado:** afxtoolbarfontcombobox.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton Class](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCFontInfo Class](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)   
 [Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)