---
title: "CMFCCaptionBar (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCCaptionBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCCaptionBar (clase)"
ms.assetid: acb54d5f-14ff-4c96-aeb3-7717cf566d9a
caps.latest.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 30
---
# CMFCCaptionBar (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un objeto de `CMFCCaptionBar` es una barra de controles que puede mostrar tres elementos: un botón, una etiqueta de texto, y un mapa de bits.  Puede mostrar un solo elemento de cada tipo al mismo tiempo.  Puede alinear cada elemento a la izquierda o los bordes derecho del control o con el centro.  También puede aplicar un plano o un estilo 3D a la parte superior y en el borde inferior de la barra de título.  
  
## Sintaxis  
  
```  
class CMFCCaptionBar : public CPane  
```  
  
## Members  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMFCCaptionBar::Create](../Topic/CMFCCaptionBar::Create.md)|Crear el control de barra de título y lo asocia al objeto de `CMFCCaptionBar`.|  
|[CMFCCaptionBar::DoesAllowDynInsertBefore](../Topic/CMFCCaptionBar::DoesAllowDynInsertBefore.md)|Indica si otro panel se puede insertar dinámicamente entre la barra de título y su marco primario.  \(Reemplaza [CBasePane::DoesAllowDynInsertBefore](../Topic/CBasePane::DoesAllowDynInsertBefore.md).\)|  
|[CMFCCaptionBar::EnableButton](../Topic/CMFCCaptionBar::EnableButton.md)|Habilita o deshabilita el botón de la barra de título.|  
|[CMFCCaptionBar::GetAlignment](../Topic/CMFCCaptionBar::GetAlignment.md)|Devuelve la alineación del elemento especificado.|  
|[CMFCCaptionBar::GetBorderSize](../Topic/CMFCCaptionBar::GetBorderSize.md)|Devuelve el tamaño del borde de la barra de título.|  
|[CMFCCaptionBar::GetButtonRect](../Topic/CMFCCaptionBar::GetButtonRect.md)|Recupera el rectángulo delimitador del botón en la barra de título.|  
|[CMFCCaptionBar::GetMargin](../Topic/CMFCCaptionBar::GetMargin.md)|Devuelve la distancia entre el borde de los elementos de la barra de título y el borde del control de barra de título.|  
|[CMFCCaptionBar::IsMessageBarMode](../Topic/CMFCCaptionBar::IsMessageBarMode.md)|Especifica si la barra de título está en modo de barra de mensajes.|  
|[CMFCCaptionBar::RemoveBitmap](../Topic/CMFCCaptionBar::RemoveBitmap.md)|Quita la imagen de mapa de bits de la barra de título.|  
|[CMFCCaptionBar::RemoveButton](../Topic/CMFCCaptionBar::RemoveButton.md)|Quita el botón de la barra de título.|  
|[CMFCCaptionBar::RemoveIcon](../Topic/CMFCCaptionBar::RemoveIcon.md)|Quita el icono de la barra de título.|  
|[CMFCCaptionBar::RemoveText](../Topic/CMFCCaptionBar::RemoveText.md)|Quita el etiqueta de texto de la barra de título.|  
|[CMFCCaptionBar::SetBitmap](../Topic/CMFCCaptionBar::SetBitmap.md)|Establece la imagen de mapa de bits de la barra de título.|  
|[CMFCCaptionBar::SetBorderSize](../Topic/CMFCCaptionBar::SetBorderSize.md)|Establece el tamaño del borde de la barra de título.|  
|[CMFCCaptionBar::SetButton](../Topic/CMFCCaptionBar::SetButton.md)|Establece el botón de la barra de título.|  
|[CMFCCaptionBar::SetButtonPressed](../Topic/CMFCCaptionBar::SetButtonPressed.md)|Especifica si el botón permanece presionado.|  
|[CMFCCaptionBar::SetButtonToolTip](../Topic/CMFCCaptionBar::SetButtonToolTip.md)|Establece la información sobre herramientas para el botón.|  
|[CMFCCaptionBar::SetFlatBorder](../Topic/CMFCCaptionBar::SetFlatBorder.md)|Establece el estilo de borde de la barra de título.|  
|[CMFCCaptionBar::SetIcon](../Topic/CMFCCaptionBar::SetIcon.md)|Establece el icono de una barra de título.|  
|[CMFCCaptionBar::SetImageToolTip](../Topic/CMFCCaptionBar::SetImageToolTip.md)|Establece la información sobre herramientas para la imagen de la barra de título.|  
|[CMFCCaptionBar::SetMargin](../Topic/CMFCCaptionBar::SetMargin.md)|Establece la distancia entre el borde del elemento de la barra de título y el borde del control de barra de título.|  
|[CMFCCaptionBar::SetText](../Topic/CMFCCaptionBar::SetText.md)|Establece el etiqueta de texto de la barra de título.|  
  
### Métodos protegidos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMFCCaptionBar::OnDrawBackground](../Topic/CMFCCaptionBar::OnDrawBackground.md)|Llamado por el marco para rellenar el fondo de la barra de título.|  
|[CMFCCaptionBar::OnDrawBorder](../Topic/CMFCCaptionBar::OnDrawBorder.md)|Llamado por el marco para dibujar el borde de la barra de título.|  
|[CMFCCaptionBar::OnDrawButton](../Topic/CMFCCaptionBar::OnDrawButton.md)|Llamado por el marco para dibujar el botón de la barra de título.|  
|[CMFCCaptionBar::OnDrawImage](../Topic/CMFCCaptionBar::OnDrawImage.md)|Llamado por el marco para dibujar la imagen de la barra de título.|  
|[CMFCCaptionBar::OnDrawText](../Topic/CMFCCaptionBar::OnDrawText.md)|Llamado por el marco para dibujar el texto de la barra de título.|  
  
### Miembros de datos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMFCCaptionBar::m\_clrBarBackground](../Topic/CMFCCaptionBar::m_clrBarBackground.md)|El color de fondo de la barra de título.|  
|[CMFCCaptionBar::m\_clrBarBorder](../Topic/CMFCCaptionBar::m_clrBarBorder.md)|Color del borde de la barra de título.|  
|[CMFCCaptionBar::m\_clrBarText](../Topic/CMFCCaptionBar::m_clrBarText.md)|Color del texto de la barra de título.|  
  
## Comentarios  
 Para crear una barra de título, siga estos pasos:  
  
1.  Cree el objeto de `CMFCCaptionBar`.  Normalmente, se agrega la barra de título a una clase de ventana de marco.  
  
2.  Llame al método de [CMFCCaptionBar::Create](../Topic/CMFCCaptionBar::Create.md) para crear el control de barra de título y para adjuntarlo al objeto de `CMFCCaptionBar`.  
  
3.  Llame a [CMFCCaptionBar::SetButton](../Topic/CMFCCaptionBar::SetButton.md), [CMFCCaptionBar::SetText](../Topic/CMFCCaptionBar::SetText.md), [CMFCCaptionBar::SetIcon](../Topic/CMFCCaptionBar::SetIcon.md), y [CMFCCaptionBar::SetBitmap](../Topic/CMFCCaptionBar::SetBitmap.md) para establecer los elementos de la barra de título.  
  
 Cuando se establece el elemento de botón, debe asignar un identificador de comando al botón.  Cuando el usuario hace clic en el botón, la barra de título enruta los mensajes de `WM_COMMAND` que tienen este identificador a la ventana de marco principal.  
  
 La barra de título también puede funcionar en modo de barra de mensajes, que emula la barra de mensajes que aparece en las aplicaciones de Microsoft Office 2007.  En modo de barra de mensajes, la barra de título muestra un mapa de bits, un mensaje, y un botón \(que abra normalmente un cuadro de diálogo\). Puede asignar una información sobre herramientas al mapa de bits.  
  
 Para habilitar el modo de la barra de mensajes, la llamada a [CMFCCaptionBar::Create](../Topic/CMFCCaptionBar::Create.md) y establecer el cuarto parámetro \(bIsMessageBarMode\) a `TRUE`.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar varios métodos en la clase de `CMFCCaptionBar`.  El ejemplo muestra cómo crear un control de la barra de título, establece un borde 3D de la barra de título, establece la distancia, en píxeles, entre el borde de los elementos de la barra de título y el borde del control de barra de título, establece el botón de la barra de título, establece la información sobre herramientas para el botón, establece el etiqueta de texto de la barra de título, establece la imagen de mapa de bits de la barra de título, y establece la información sobre herramientas para la imagen en la barra de título.  Este fragmento de código es parte de [Ejemplo 2007 de demostración de MS Office](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#1](../../mfc/reference/codesnippet/CPP/cmfccaptionbar-class_1.h)]  
[!code-cpp[NVC_MFC_MSOffice2007Demo#2](../../mfc/reference/codesnippet/CPP/cmfccaptionbar-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)  
  
## Requisitos  
 **Encabezado:** afxcaptionbar.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)