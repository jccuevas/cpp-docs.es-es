---
title: "CMFCColorDialog Class | Microsoft Docs"
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
  - "CMFCColorDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCColorDialog class"
  - "CMFCColorDialog::m_bIsMyPalette data member"
  - "CMFCColorDialog::m_bPickerMode data member"
  - "CMFCColorDialog::m_btnColorSelect data member"
  - "CMFCColorDialog::m_CurrentColor data member"
  - "CMFCColorDialog::m_hcurPicker data member"
  - "CMFCColorDialog::m_NewColor data member"
  - "CMFCColorDialog::m_pColourSheetOne data member"
  - "CMFCColorDialog::m_pColourSheetTwo data member"
  - "CMFCColorDialog::m_pPalette data member"
  - "CMFCColorDialog::m_pPropSheet data member"
  - "CMFCColorDialog::m_wndColors data member"
  - "CMFCColorDialog::m_wndStaticPlaceHolder data member"
  - "CMFCColorDialog::PreTranslateMessage method"
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
caps.latest.revision: 30
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCColorDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCColorDialog` representa un cuadro de diálogo de selección de color.  
  
## Sintaxis  
  
```  
class CMFCColorDialog : public CDialogEx  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorDialog::CMFCColorDialog](../Topic/CMFCColorDialog::CMFCColorDialog.md)|Crea un objeto `CMFCColorDialog`.|  
|`CMFCColorDialog::~CMFCColorDialog`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorDialog::GetColor](../Topic/CMFCColorDialog::GetColor.md)|Devuelve el color seleccionado actual.|  
|[CMFCColorDialog::GetPalette](../Topic/CMFCColorDialog::GetPalette.md)|Devuelve la paleta de colores.|  
|`CMFCColorDialog::PreTranslateMessage`|Traduce mensajes de ventana antes de que se envíen a las funciones de [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y de [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows.  Para la sintaxis y más información, vea [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md).  \(Reemplaza `CDialogEx::PreTranslateMessage`.\)|  
|[CMFCColorDialog::RebuildPalette](../Topic/CMFCColorDialog::RebuildPalette.md)|Derivar una paleta de la tabla del sistema.|  
|[CMFCColorDialog::SetCurrentColor](../Topic/CMFCColorDialog::SetCurrentColor.md)|Establece el color seleccionado actual.|  
|[CMFCColorDialog::SetNewColor](../Topic/CMFCColorDialog::SetNewColor.md)|Establece el color el equivalente a un valor especificado RGB.|  
|[CMFCColorDialog::SetPageOne](../Topic/CMFCColorDialog::SetPageOne.md)|Selecciona un valor RGB para la primera página de propiedades.|  
|[CMFCColorDialog::SetPageTwo](../Topic/CMFCColorDialog::SetPageTwo.md)|Selecciona un valor RGB para la segunda página de propiedades.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|`m_bIsMyPalette`|`TRUE` si el cuadro de diálogo de selección de color utiliza su propia paleta colores, o `FALSE` si el cuadro de diálogo usa una tabla que se especifica en el constructor de `CMFCColorDialog` .|  
|`m_bPickerMode`|`TRUE` mientras el usuario está seleccionando el color del cuadro de diálogo de selección; si no, `FALSE`.|  
|`m_btnColorSelect`|El botón del color seleccionado por el usuario.|  
|`m_CurrentColor`|Color seleccionado actualmente.|  
|`m_hcurPicker`|Cursor que se utiliza para elegir un color.|  
|`m_NewColor`|El color seleccionado previsto, que se pueden seleccionar o revertir permanentemente al color original.|  
|`m_pColourSheetOne`|Un puntero a la primera página de propiedades de la hoja de propiedades de selección de color.|  
|`m_pColourSheetTwo`|Un puntero a la segunda página de propiedades de la hoja de propiedades de selección de color.|  
|`m_pPalette`|La paleta lógica actual.|  
|`m_pPropSheet`|Un puntero a la hoja de propiedades del cuadro de diálogo de selección de color.|  
|`m_wndColors`|Un objeto de control Selector de colores.|  
|`m_wndStaticPlaceHolder`|Un control estático que es un marcador de la hoja de propiedades de Selector de colores.|  
  
## Comentarios  
 El cuadro de diálogo de selección de color se muestra como hoja de propiedades con dos páginas.  En la primera página, seleccione un color estándar de la tabla del sistema; en la segunda página, se selecciona un color personalizado.  
  
 Puede construir un objeto de `CMFCColorDialog` en la pila y llamar después a `DoModal`, pasando el color inicial como parámetro al constructor de `CMFCColorDialog` .  El cuadro de diálogo de selección de color crea varios objetos de [CMFCColorPickerCtrl Class](../../mfc/reference/cmfccolorpickerctrl-class.md) para tratar cada paleta de colores.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo configurar un diálogo color mediante varios métodos en la clase de `CMFCColorDialog` .  El ejemplo muestra cómo establecer la actual y los nuevos colores del diálogo, y cómo establecer los componentes rojo, verde, y azul del color seleccionado en las dos páginas de propiedades de diálogo color.  Este ejemplo forma parte de [nuevo ejemplo de Controles](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/CPP/cmfccolordialog-class_1.cpp)]  
  
## Requisitos  
 **encabezado:** afxcolordialog.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCColorPickerCtrl Class](../../mfc/reference/cmfccolorpickerctrl-class.md)