---
title: "CMFCDesktopAlertWnd Class | Microsoft Docs"
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
  - "CMFCDesktopAlertWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDesktopAlertWnd class"
ms.assetid: 73a2dd7b-ea84-4ae2-9830-7cf6e8dd2425
caps.latest.revision: 33
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCDesktopAlertWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCDesktopAlertWnd` implementa la funcionalidad de un cuadro de diálogo no modal que aparece en la pantalla para informar al usuario sobre un evento.  
  
## Sintaxis  
  
```  
class CMFCDesktopAlertWnd : public CWnd  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCDesktopAlertWnd::Create](../Topic/CMFCDesktopAlertWnd::Create.md)|Crea e inicializa la ventana de alerta de escritorio.|  
|[CMFCDesktopAlertWnd::GetAnimationSpeed](../Topic/CMFCDesktopAlertWnd::GetAnimationSpeed.md)|devuelve la velocidad de la animación.|  
|[CMFCDesktopAlertWnd::GetAnimationType](../Topic/CMFCDesktopAlertWnd::GetAnimationType.md)|Devuelve el tipo de animación.|  
|[CMFCDesktopAlertWnd::GetAutoCloseTime](../Topic/CMFCDesktopAlertWnd::GetAutoCloseTime.md)|Devuelve el tiempo de espera de auto\-cierre.|  
|[CMFCDesktopAlertWnd::GetCaptionHeight](../Topic/CMFCDesktopAlertWnd::GetCaptionHeight.md)|Devuelve el alto de la leyenda.|  
|[CMFCDesktopAlertWnd::GetDialogSize](../Topic/CMFCDesktopAlertWnd::GetDialogSize.md)||  
|[CMFCDesktopAlertWnd::GetLastPos](../Topic/CMFCDesktopAlertWnd::GetLastPos.md)|Devuelve la posición válida de la última ventana de alerta de escritorio respecto a la pantalla.|  
|[CMFCDesktopAlertWnd::GetTransparency](../Topic/CMFCDesktopAlertWnd::GetTransparency.md)|Devuelve el nivel de transparencia.|  
|[CMFCDesktopAlertWnd::HasSmallCaption](../Topic/CMFCDesktopAlertWnd::HasSmallCaption.md)|Determina si la ventana de alerta de escritorio se muestra con el pequeño leyenda.|  
|[CMFCDesktopAlertWnd::OnBeforeShow](../Topic/CMFCDesktopAlertWnd::OnBeforeShow.md)||  
|[CMFCDesktopAlertWnd::OnClickLinkButton](../Topic/CMFCDesktopAlertWnd::OnClickLinkButton.md)|Llamado por el marco cuando el usuario hace clic en un botón de vínculo ubicado en el menú de alerta de escritorio.|  
|[CMFCDesktopAlertWnd::OnCommand](../Topic/CMFCDesktopAlertWnd::OnCommand.md)|El marco de trabajo llama a esta función miembro cuando el usuario selecciona un elemento de un menú, cuando un control secundario envía un mensaje de notificación, o cuando se convierte una tecla de aceleración.  \(Reemplaza [CWnd::OnCommand](../Topic/CWnd::OnCommand.md).\)|  
|[CMFCDesktopAlertWnd::OnDraw](../Topic/CMFCDesktopAlertWnd::OnDraw.md)||  
|[CMFCDesktopAlertWnd::ProcessCommand](../Topic/CMFCDesktopAlertWnd::ProcessCommand.md)||  
|[CMFCDesktopAlertWnd::SetAnimationSpeed](../Topic/CMFCDesktopAlertWnd::SetAnimationSpeed.md)|establece la nueva velocidad de la animación.|  
|[CMFCDesktopAlertWnd::SetAnimationType](../Topic/CMFCDesktopAlertWnd::SetAnimationType.md)|Establece el tipo de animación.|  
|[CMFCDesktopAlertWnd::SetAutoCloseTime](../Topic/CMFCDesktopAlertWnd::SetAutoCloseTime.md)|Establece el tiempo de espera de auto\-cierre.|  
|[CMFCDesktopAlertWnd::SetSmallCaption](../Topic/CMFCDesktopAlertWnd::SetSmallCaption.md)|Cambia entre leyendas pequeñas y normales.|  
|[CMFCDesktopAlertWnd::SetTransparency](../Topic/CMFCDesktopAlertWnd::SetTransparency.md)|Establece el nivel de transparencia.|  
  
## Comentarios  
 Una ventana de alerta de escritorio puede ser transparente, puede aparecer con efectos de animación, y puede desaparecer \(después de un retraso especificado o cuando el usuario lo descarta haciendo clic en el botón cerrar\).  
  
 Una ventana de alerta de escritorio puede contener también un diálogo predeterminado que a su vez contiene un icono, el texto del mensaje \(una etiqueta\), y un vínculo.  Alternativamente, una ventana de alerta de escritorio puede contener un diálogo de los recursos de la aplicación.  
  
 Crea una ventana de alerta de escritorio en dos pasos.  Primero, llame al constructor para crear el objeto de `CMFCDesktopAlertWnd` .  En segundo lugar, llame a la función miembro de [CMFCDesktopAlertWnd::Create](../Topic/CMFCDesktopAlertWnd::Create.md) para crear la ventana y para adjuntarla al objeto de `CMFCDesktopAlertWnd` .  
  
 El objeto de `CMFCDesktopAlertWnd` crea un cuadro de diálogo secundario especial que rellene el área cliente de la ventana de alerta de escritorio.  el diálogo posee todos los controles que se colocan en él.  
  
 Para mostrar un cuadro de diálogo personalizado en la ventana emergente, siga estos pasos:  
  
1.  derive una clase de `CMFCDesktopAlertDialog`.  
  
2.  Cree una plantilla secundaria del cuadro de diálogo en los recursos.  
  
3.  Llame a [CMFCDesktopAlertWnd::Create](../Topic/CMFCDesktopAlertWnd::Create.md) mediante el Id. de recurso de plantilla de cuadro de diálogo y un puntero a la información de la clase en tiempo de ejecución de la clase derivada.  
  
4.  Programar el cuadro de diálogo personalizado para controlar todas las notificaciones que proceden de los controles de hospedados, o programar los controles hospedados controlar estas notificaciones directamente.  
  
 Utilice las siguientes funciones para controlar el comportamiento de la ventana de alerta de escritorio:  
  
-   Establezca la animación tipo llamando a [CMFCDesktopAlertWnd::SetAnimationType](../Topic/CMFCDesktopAlertWnd::SetAnimationType.md).  Inclusión válida de las opciones revela, entrega, y se desvanece.  
  
-   Establezca la velocidad de fotograma animación llamando a [CMFCDesktopAlertWnd::SetAnimationSpeed](../Topic/CMFCDesktopAlertWnd::SetAnimationSpeed.md).  
  
-   Establezca la transparencia de llamando a [CMFCDesktopAlertWnd::SetTransparency](../Topic/CMFCDesktopAlertWnd::SetTransparency.md).  
  
-   Cambie el tamaño de la leyenda a pequeño llamando a [CMFCDesktopAlertWnd::SetSmallCaption](../Topic/CMFCDesktopAlertWnd::SetSmallCaption.md).  El pequeño leyenda es 7 píxeles de alto.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar varios métodos en la clase de `CMFCDesktopAlertWnd` para configurar un objeto de `CMFCDesktopAlertWnd` .  El ejemplo muestra cómo establecer un tipo de animación, establece la transparencia de la ventana emergente, especifica que la ventana alerta muestra un pequeño leyenda, y establece el tiempo que cierre que transcurre antes de la ventana alerta automáticamente.  El ejemplo también se muestra cómo crear e inicializar la ventana de alerta de escritorio.  Este fragmento de código es parte de [Ejemplo de demostración de alerta de escritorio](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/CPP/cmfcdesktopalertwnd-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)  
  
## Requisitos  
 **encabezado:** afxDesktopAlertWnd.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertWndInfo Class](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)   
 [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)