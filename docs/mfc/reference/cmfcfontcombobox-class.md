---
title: "CMFCFontComboBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCFontComboBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCFontComboBox class"
  - "CMFCFontComboBox::CompareItem method"
  - "CMFCFontComboBox::DrawItem method"
  - "CMFCFontComboBox::MeasureItem method"
  - "CMFCFontComboBox::PreTranslateMessage method"
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
caps.latest.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 31
---
# CMFCFontComboBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCFontComboBox` crea un control de cuadro combinado que contiene una lista de fuentes.  
  
## Sintaxis  
  
```  
class CMFCFontComboBox : public CComboBox  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCFontComboBox::CMFCFontComboBox](../Topic/CMFCFontComboBox::CMFCFontComboBox.md)|Crea un objeto `CMFCFontComboBox`.|  
|`CMFCFontComboBox::~CMFCFontComboBox`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCFontComboBox::CompareItem`|Llamado por el marco para determinar la posición relativa de un nuevo elemento en el cuadro de lista ordenada del control actual de cuadro combinado de la fuente.  \(Reemplaza [CComboBox::CompareItem](../Topic/CComboBox::CompareItem.md).\)|  
|`CMFCFontComboBox::DrawItem`|Llamado por el marco para dibujar un elemento especificado en el control actual del cuadro combinado de la fuente.  \(Reemplaza [CComboBox::DrawItem](../Topic/CComboBox::DrawItem.md).\)|  
|[CMFCFontComboBox::GetSelFont](../Topic/CMFCFontComboBox::GetSelFont.md)|Recupera información sobre fuentes actualmente seleccionado.|  
|`CMFCFontComboBox::MeasureItem`|Llamado por el marco para informar a Windows las dimensiones del cuadro de lista del control actual de cuadro combinado de la fuente.  \(Reemplaza [CComboBox::MeasureItem](../Topic/CComboBox::MeasureItem.md).\)|  
|`CMFCFontComboBox::PreTranslateMessage`|Traduce mensajes de ventana antes de que se envíen a las funciones de [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y de [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows.  \(Reemplaza [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md).\)|  
|[CMFCFontComboBox::SelectFont](../Topic/CMFCFontComboBox::SelectFont.md)|Selecciona la fuente que coincide con los criterios especificados en el cuadro combinado de la fuente.|  
|[CMFCFontComboBox::Setup](../Topic/CMFCFontComboBox::Setup.md)|Inicializa la lista de elementos del cuadro combinado de la fuente.|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCFontComboBox::m\_bDrawUsingFont](../Topic/CMFCFontComboBox::m_bDrawUsingFont.md)|Indica al marco que fuente utilizar para dibujar las etiquetas de elemento en el cuadro combinado actual de la fuente.|  
  
## Comentarios  
 Para utilizar un objeto de `CMFCFontComboBox` en un cuadro de diálogo, agregue una variable de `CMFCFontComboBox` a la del cuadro de diálogo.  A continuación en el método de `OnInitDialog` de la del cuadro de diálogo, llame al método de [CMFCFontComboBox::Setup](../Topic/CMFCFontComboBox::Setup.md) para inicializar la lista de elementos en el control de cuadro combinado.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CComboBox](../../mfc/reference/ccombobox-class.md)  
  
 [CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)  
  
## Requisitos  
 **encabezado:** afxfontcombobox.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [CMFCFontInfo Class](../../mfc/reference/cmfcfontinfo-class.md)