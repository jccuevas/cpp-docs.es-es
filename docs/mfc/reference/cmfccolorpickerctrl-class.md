---
title: "CMFCColorPickerCtrl Class | Microsoft Docs"
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
  - "CMFCColorPickerCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCColorPickerCtrl class"
ms.assetid: b9bbd03c-beb0-4b55-9765-9985fd05e5dc
caps.latest.revision: 33
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCColorPickerCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCColorPickerCtrl` proporciona funcionalidad para un control que se utiliza para seleccionar colores.  
  
## Sintaxis  
  
```  
class CMFCColorPickerCtrl : public CButton  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorPickerCtrl::CMFCColorPickerCtrl](../Topic/CMFCColorPickerCtrl::CMFCColorPickerCtrl.md)|Crea un objeto `CMFCColorPickerCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorPickerCtrl::GetColor](../Topic/CMFCColorPickerCtrl::GetColor.md)|Recupera el color que el usuario selecciona.|  
|[CMFCColorPickerCtrl::GetHLS](../Topic/CMFCColorPickerCtrl::GetHLS.md)|Recupera los valores de matiz, de luminancia y de saturación del color que el usuario selecciona.|  
|[CMFCColorPickerCtrl::GetHue](../Topic/CMFCColorPickerCtrl::GetHue.md)|Recupera el componente de matiz del color que el usuario selecciona.|  
|[CMFCColorPickerCtrl::GetLuminance](../Topic/CMFCColorPickerCtrl::GetLuminance.md)|Recupera el componente de luminancia de color que el usuario selecciona.|  
|[CMFCColorPickerCtrl::GetSaturation](../Topic/CMFCColorPickerCtrl::GetSaturation.md)|Recupera el componente de la saturación del color que el usuario selecciona.|  
|[CMFCColorPickerCtrl::SelectCellHexagon](../Topic/CMFCColorPickerCtrl::SelectCellHexagon.md)|Establece el color actual al color definido por los componentes de color especificados RGB o el hexágono especificado de la celda.|  
|[CMFCColorPickerCtrl::SetColor](../Topic/CMFCColorPickerCtrl::SetColor.md)|Establece el color actual en el valor del color especificado RGB.|  
|[CMFCColorPickerCtrl::SetHLS](../Topic/CMFCColorPickerCtrl::SetHLS.md)|Establece el color actual en el valor del color especificado de HLS.|  
|[CMFCColorPickerCtrl::SetHue](../Topic/CMFCColorPickerCtrl::SetHue.md)|Cambia el componente de matiz del color seleccionado actualmente.|  
|[CMFCColorPickerCtrl::SetLuminance](../Topic/CMFCColorPickerCtrl::SetLuminance.md)|Cambia el componente de luminancia de color seleccionado actualmente.|  
|[CMFCColorPickerCtrl::SetLuminanceBarWidth](../Topic/CMFCColorPickerCtrl::SetLuminanceBarWidth.md)|Establece el ancho de la barra de luminancia en el control selector de colores.|  
|[CMFCColorPickerCtrl::SetOriginalColor](../Topic/CMFCColorPickerCtrl::SetOriginalColor.md)|Establece el color seleccionado inicial.|  
|[CMFCColorPickerCtrl::SetPalette](../Topic/CMFCColorPickerCtrl::SetPalette.md)|establece la paleta de colores actual.|  
|[CMFCColorPickerCtrl::SetSaturation](../Topic/CMFCColorPickerCtrl::SetSaturation.md)|Cambia el componente de la saturación del color seleccionado actualmente.|  
|[CMFCColorPickerCtrl::SetType](../Topic/CMFCColorPickerCtrl::SetType.md)|Establece el tipo de control selector de colores para mostrar.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorPickerCtrl::DrawCursor](../Topic/CMFCColorPickerCtrl::DrawCursor.md)|Llamado por el marco antes de cursor que señala al color seleccionado se muestra.|  
  
## Comentarios  
 Los colores estándar son seleccionadas de una paleta de colores hexagonal, y los colores personalizados son seleccionadas de una barra de luminancia donde los colores se especifican mediante rojo\/verde\/azul notación o notación de matiz\/satuaration\/de luminancia.  
  
 la ilustración siguiente describe varios objetos de `CMFCColorPickerCtrl` .  
  
 ![Cuadro de diálogo CMFCColorPickerCtrl](../../mfc/reference/media/colorpicker.png "ColorPicker")  
  
 `CMFCColorPickerCtrl` admite dos pares de estilos.  Los estilos de HEX. y de HEX\_GREYSCALE son adecuados para la selección de color estándar.  Los estilos de PICKER y la LUMINANCIA son adecuados para la selección de colores personalizada.  
  
 Realice los pasos siguientes para incorporar el control de `CMFCColorPickerCtrl` en el cuadro de diálogo:  
  
1.  Si utiliza **ClassWizard**, inserte un nuevo control button a la plantilla de cuadro de diálogo \(como la clase de `CMFCColorPickerCtrl` se hereda de la clase de `CButton` \).  
  
2.  Inserte una variable miembro que está asociada al nuevo control button a la clase del cuadro de diálogo.  A continuación cambie la variable de tipos `CButton` a `CMFCColorPickerCtrl`.  
  
3.  Inserte el controlador de mensajes de `WM_INITDIALOG` para la clase de cuadro de diálogo.  En el controlador, establezca el tipo, la paleta, y el color seleccionados inicial del control de `CMFCColorPickerCtrl` .  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo configurar un objeto de `CMFCColorPickerCtrl` mediante varios métodos en la clase de `CMFCColorPickerCtrl` .  El ejemplo muestra cómo establecer el tipo de control de selección, y cómo establecer el color, matiz, luminancia, y saturación.  El ejemplo forma parte de [nuevo ejemplo de Controles](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#4](../../mfc/reference/codesnippet/CPP/cmfccolorpickerctrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#5](../../mfc/reference/codesnippet/CPP/cmfccolorpickerctrl-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)  
  
## Requisitos  
 **encabezado:** afxcolorpickerctrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCColorDialog Class](../../mfc/reference/cmfccolordialog-class.md)