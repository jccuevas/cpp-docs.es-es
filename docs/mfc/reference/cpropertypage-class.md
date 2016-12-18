---
title: "CPropertyPage Class | Microsoft Docs"
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
  - "CPropertyPage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPropertyPage class"
  - "cuadros de diálogo, pestañas"
  - "páginas de propiedades, CPropertyPage class"
  - "cuadros de diálogo con fichas"
ms.assetid: d9000a21-aa81-4530-85d9-f43432afb4dc
caps.latest.revision: 25
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPropertyPage Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

representa las páginas individuales de una hoja de propiedades, si no conocidas como cuadro de diálogo de la ficha.  
  
## Sintaxis  
  
```  
class CPropertyPage : public CDialog  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPropertyPage::CPropertyPage](../Topic/CPropertyPage::CPropertyPage.md)|Crea un objeto `CPropertyPage`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPropertyPage::CancelToClose](../Topic/CPropertyPage::CancelToClose.md)|Cambia el botón ACEPTAR para leer cierre, y deshabilita el botón Cancelar, después de un cambio irrecuperable en la página de una hoja de propiedades modal.|  
|[CPropertyPage::Construct](../Topic/CPropertyPage::Construct.md)|Crea un objeto `CPropertyPage`.  Utilice `Construct` si desea especificar los parámetros en tiempo de ejecución, o si está utilizando las matrices.|  
|[CPropertyPage::GetPSP](../Topic/CPropertyPage::GetPSP.md)|recupera la estructura de Windows [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548) asociado con el objeto de `CPropertyPage` .|  
|[CPropertyPage::OnApply](../Topic/CPropertyPage::OnApply.md)|Llamado por el marco cuando se hace clic en el botón de Menú de aplicar.|  
|[CPropertyPage::OnCancel](../Topic/CPropertyPage::OnCancel.md)|Llamado por el marco cuando se hace clic en el botón cancel.|  
|[CPropertyPage::OnKillActive](../Topic/CPropertyPage::OnKillActive.md)|Llamado por el marco cuando la página actual ya no la página activa.  Aquí se realiza la validación de los datos.|  
|[CPropertyPage::OnOK](../Topic/CPropertyPage::OnOK.md)|Llamado por el marco cuando aplica OK, Now, o el botón cerrar se haga clic en.|  
|[CPropertyPage::OnQueryCancel](../Topic/CPropertyPage::OnQueryCancel.md)|Llamado por el marco cuando se hace clic en el botón Cancelar, y antes de cancelación ha tenido lugar.|  
|[CPropertyPage::OnReset](../Topic/CPropertyPage::OnReset.md)|Llamado por el marco cuando se hace clic en el botón cancel.|  
|[CPropertyPage::OnSetActive](../Topic/CPropertyPage::OnSetActive.md)|Llamado por el marco cuando la página se hace la página activa.|  
|[CPropertyPage::OnWizardBack](../Topic/CPropertyPage::OnWizardBack.md)|Llamado por el marco cuando se hace clic en el botón atrás mientras utiliza una hoja de propiedades de asistente\-tipo.|  
|[CPropertyPage::OnWizardFinish](../Topic/CPropertyPage::OnWizardFinish.md)|Llamado por el marco cuando se hace clic en el botón de final siempre mediante una hoja de propiedades de asistente\-tipo.|  
|[CPropertyPage::OnWizardNext](../Topic/CPropertyPage::OnWizardNext.md)|Llamado por el marco cuando se hace clic en el botón siguiente mientras utiliza una hoja de propiedades de asistente\-tipo.|  
|[CPropertyPage::QuerySiblings](../Topic/CPropertyPage::QuerySiblings.md)|Transmite el mensaje cada página de la hoja de propiedades.|  
|[CPropertyPage::SetModified](../Topic/CPropertyPage::SetModified.md)|Llamada para activar o desactivar el botón de Menú de aplicar.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPropertyPage::m\_psp](../Topic/CPropertyPage::m_psp.md)|la estructura de Windows [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548) .  Proporciona acceso a los parámetros básicos de la página de propiedades.|  
  
## Comentarios  
 Como con cuadros de diálogo estándar, derive una clase de `CPropertyPage` para cada página de la hoja de propiedades.  Para utilizar `CPropertyPage`\- objetos derivados, primero cree un objeto de [CPropertySheet](../../mfc/reference/cpropertysheet-class.md) , y luego cree un objeto para cada página que entre en la hoja de propiedades.  Llame a [CPropertySheet:: AddPage](../Topic/CPropertySheet::AddPage.md) para cada página de la hoja, y envíe la hoja de propiedades llamando a [CPropertySheet:: DoModal](../Topic/CPropertySheet::DoModal.md) para una hoja de propiedades modal, o [CPropertySheet:: Crear](../Topic/CPropertySheet::Create.md) para una hoja de propiedades no modal.  
  
 Puede crear un tipo de cuadro de diálogo de la ficha denominado un asistente, que consta de una hoja de propiedades con una secuencia de páginas de propiedades destinados a través de los pasos de una operación, como configuración de un dispositivo o crear un boletín.  En un cuadro de diálogo de la ficha del asistente\-tipo, las páginas de propiedades no tienen pestañas, y sólo una página de la propiedad es visible al mismo tiempo.  Además, en lugar de tener ACEPTAR y utilice los botones de Menú, un asistente\-tipo que el cuadro de diálogo de la ficha tiene un botón atrás, un botón de Siguiente o end, y un botón de cancelación.  
  
 Para obtener más información sobre el establecimiento de una hoja de propiedades como este asistente, vea [CPropertySheet:: SetWizardMode](../Topic/CPropertySheet::SetWizardMode.md).  Para obtener más información sobre cómo utilizar los objetos de `CPropertyPage` , vea el artículo [hojas de propiedades y páginas de propiedades](../../mfc/property-sheets-and-property-pages-in-mfc.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `CPropertyPage`  
  
## Requisitos  
 **encabezado:** afxdlgs.h  
  
## Vea también  
 [ejemplo CMNCTRL1 de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo CMNCTRL2 de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo PROPDLG de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo SNAPVW de MFC](../../top/visual-cpp-samples.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CPropertySheet Class](../../mfc/reference/cpropertysheet-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)   
 [CPropertySheet::SetWizardMode](../Topic/CPropertySheet::SetWizardMode.md)