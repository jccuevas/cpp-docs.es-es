---
title: "CMFCDesktopAlertWndInfo Class | Microsoft Docs"
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
  - "CMFCDesktopAlertWndInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDesktopAlertWndInfo class"
ms.assetid: 5c9bb84e-6c96-4748-8e74-6951b6ae8e84
caps.latest.revision: 26
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCDesktopAlertWndInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase `CMFCDesktopAlertWndInfo` se utiliza junto con [CMFCDesktopAlertWnd Class](../../mfc/reference/cmfcdesktopalertwnd-class.md).  Especifica los controles que se muestran si la ventana de alerta de escritorio surge.  
  
## Sintaxis  
  
```  
class CMFCDesktopAlertWndInfo  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCDesktopAlertWndInfo::~CMFCDesktopAlertWndInfo`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCDesktopAlertWndInfo::operator\=](../Topic/CMFCDesktopAlertWndInfo::operator=.md)||  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCDesktopAlertWndInfo::m\_hIcon](../Topic/CMFCDesktopAlertWndInfo::m_hIcon.md)|Un identificador al icono que se muestra.|  
|[CMFCDesktopAlertWndInfo::m\_nURLCmdID](../Topic/CMFCDesktopAlertWndInfo::m_nURLCmdID.md)|El id. de comando asociado a un vínculo en el escritorio alerta la ventana.|  
|[CMFCDesktopAlertWndInfo::m\_strText](../Topic/CMFCDesktopAlertWndInfo::m_strText.md)|El texto que se muestra en la ventana de alerta de escritorio.|  
|[CMFCDesktopAlertWndInfo::m\_strURL](../Topic/CMFCDesktopAlertWndInfo::m_strURL.md)|El vínculo que se muestra en la ventana de alerta de escritorio.|  
  
## Comentarios  
 La clase de `CMFCDesktopAlertWndInfo` se pasa al método de [CMFCDesktopAlertWnd::Create](../Topic/CMFCDesktopAlertWnd::Create.md) para especificar los elementos que se muestran en el diálogo de ventana predeterminado de alerta de escritorio.  El diálogo predeterminado puede contener tres elementos:  
  
-   Un icono, que se establece llamando a [CMFCDesktopAlertWndInfo::m\_hIcon](../Topic/CMFCDesktopAlertWndInfo::m_hIcon.md).  
  
-   Una etiqueta, o mensaje de texto, que se establece llamando a [CMFCDesktopAlertWndInfo::m\_strText](../Topic/CMFCDesktopAlertWndInfo::m_strText.md).  
  
-   Un vínculo, que se establece llamando a [CMFCDesktopAlertWndInfo::m\_strURL](../Topic/CMFCDesktopAlertWndInfo::m_strURL.md).  Para establecer el comando que se ejecuta cuando se hace clic en el vínculo, llame a [CMFCDesktopAlertWndInfo::m\_nURLCmdID](../Topic/CMFCDesktopAlertWndInfo::m_nURLCmdID.md).  
  
 Si el diálogo predeterminado no es suficiente, puede crear un diálogo personalizado y pasarlo al método de [CMFCDesktopAlertWnd::Create](../Topic/CMFCDesktopAlertWnd::Create.md) en lugar de utilizar esta clase.  Para obtener más información, vea [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md).  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar los diversos miembros de la clase de `CMFCDesktopAlertWndInfo` .  El ejemplo muestra cómo establecer el identificador al icono que se muestra, el texto que se muestra en la ventana de alerta de escritorio, el vínculo que se muestra en la ventana de alerta de escritorio, y el id. de comando asociado a un vínculo en el escritorio alerta la ventana.  Este ejemplo forma parte de [Ejemplo de demostración de alerta de escritorio](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#3](../../mfc/reference/codesnippet/CPP/cmfcdesktopalertwndinfo-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)  
  
## Requisitos  
 **encabezado:** afxDesktopAlertDialog.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertWnd Class](../../mfc/reference/cmfcdesktopalertwnd-class.md)   
 [CMFCDesktopAlertWnd::Create](../Topic/CMFCDesktopAlertWnd::Create.md)   
 [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md)