---
title: "CPropertySheet Class | Microsoft Docs"
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
  - "CPropertySheet"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPropertySheet class"
  - "cuadros de diálogo, pestañas"
  - "hojas de propiedades, CPropertySheet class"
  - "cuadros de diálogo con fichas"
ms.assetid: 8461ccff-d14f-46e0-a746-42ad642ef94e
caps.latest.revision: 30
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPropertySheet Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

representa las hojas de propiedades, también conocidas como cuadros de diálogo de la ficha.  
  
## Sintaxis  
  
```  
class CPropertySheet : public CWnd  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPropertySheet::CPropertySheet](../Topic/CPropertySheet::CPropertySheet.md)|Crea un objeto `CPropertySheet`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPropertySheet::AddPage](../Topic/CPropertySheet::AddPage.md)|agrega una página a la hoja de propiedades.|  
|[CPropertySheet::Construct](../Topic/CPropertySheet::Construct.md)|Crea un objeto `CPropertySheet`.|  
|[CPropertySheet::Create](../Topic/CPropertySheet::Create.md)|Muestra una hoja de propiedades no modal.|  
|[CPropertySheet::DoModal](../Topic/CPropertySheet::DoModal.md)|Muestra una hoja de propiedades modal.|  
|[CPropertySheet::EnableStackedTabs](../Topic/CPropertySheet::EnableStackedTabs.md)|Indica si la hoja de propiedades usar pestañas apilado o de desplazamiento.|  
|[CPropertySheet::EndDialog](../Topic/CPropertySheet::EndDialog.md)|finaliza la hoja de propiedades.|  
|[CPropertySheet::GetActiveIndex](../Topic/CPropertySheet::GetActiveIndex.md)|recupera el índice de la página activa de la hoja de propiedades.|  
|[CPropertySheet::GetActivePage](../Topic/CPropertySheet::GetActivePage.md)|devuelve el objeto de la página activa.|  
|[CPropertySheet::GetPage](../Topic/CPropertySheet::GetPage.md)|recupera un puntero a la página especificada.|  
|[CPropertySheet::GetPageCount](../Topic/CPropertySheet::GetPageCount.md)|recupera el número de páginas en la hoja de propiedades.|  
|[CPropertySheet::GetPageIndex](../Topic/CPropertySheet::GetPageIndex.md)|recupera el índice de la página especificada de la hoja de propiedades.|  
|[CPropertySheet::GetTabControl](../Topic/CPropertySheet::GetTabControl.md)|Recupera un puntero a un control de ficha.|  
|[CPropertySheet::MapDialogRect](../Topic/CPropertySheet::MapDialogRect.md)|Convierte las unidades de cuadro de diálogo de un rectángulo en unidades de la pantalla.|  
|[CPropertySheet::OnInitDialog](../Topic/CPropertySheet::OnInitDialog.md)|reemplace para aumentar la inicialización de la hoja de propiedades.|  
|[CPropertySheet::PressButton](../Topic/CPropertySheet::PressButton.md)|Simula la elección del botón especificado en una hoja de propiedades.|  
|[CPropertySheet::RemovePage](../Topic/CPropertySheet::RemovePage.md)|quita una página de la hoja de propiedades.|  
|[CPropertySheet::SetActivePage](../Topic/CPropertySheet::SetActivePage.md)|Establezca mediante programación el objeto de la página activa.|  
|[CPropertySheet::SetFinishText](../Topic/CPropertySheet::SetFinishText.md)|Establece el texto para el botón de final.|  
|[CPropertySheet::SetTitle](../Topic/CPropertySheet::SetTitle.md)|Establece la leyenda de la hoja de propiedades.|  
|[CPropertySheet::SetWizardButtons](../Topic/CPropertySheet::SetWizardButtons.md)|Habilita los botones del asistente.|  
|[CPropertySheet::SetWizardMode](../Topic/CPropertySheet::SetWizardMode.md)|habilita el modo de asistente.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPropertySheet::m\_psh](../Topic/CPropertySheet::m_psh.md)|la estructura de Windows [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546) .  Proporciona acceso a los parámetros básicos de la hoja de propiedades.|  
  
## Comentarios  
 Una hoja de propiedades consta de un objeto de `CPropertySheet` y uno o más objetos de [CPropertyPage](../../mfc/reference/cpropertypage-class.md) .  El marco muestra una hoja de propiedades como una ventana con un conjunto de índices de la ficha y un área que contiene la página actualmente seleccionado.  El usuario navega a una página determinada mediante la ficha adecuada.  
  
 `CPropertySheet` proporciona compatibilidad para la estructura expandida de [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546) introdujo en [!INCLUDE[Win98](../../mfc/reference/includes/win98_md.md)] y Windows NT 2000.  La estructura contiene marcas adicionales y miembros que admiten mediante un mapa de bits de fondo de “marca de agua”.  
  
 Para mostrar estas nuevas imágenes automáticamente en el objeto de hoja de propiedades, pase los valores válidos para las imágenes de mapa de bits y la paleta de la llamada a [CPropertySheet:: construcción](../Topic/CPropertySheet::Construct.md) o a [CPropertySheet:: CPropertySheet](../Topic/CPropertySheet::CPropertySheet.md).  
  
 aunque `CPropertySheet` no es derivado de [CDialog](../../mfc/reference/cdialog-class.md), administrar un objeto de `CPropertySheet` es como administrar un objeto de `CDialog` .  Por ejemplo, la creación de una hoja de propiedades requiere construcción dividida en dos partes: llame al constructor, y llame a [DoModal](../Topic/CPropertySheet::DoModal.md) para una hoja de propiedades modal o [Crear](../Topic/CPropertySheet::Create.md) para una hoja de propiedades no modal.  `CPropertySheet` tiene dos tipos de constructores: [CPropertySheet:: construcción](../Topic/CPropertySheet::Construct.md) y [CPropertySheet:: CPropertySheet](../Topic/CPropertySheet::CPropertySheet.md).  
  
 Cuando se crea un objeto de `CPropertySheet` , algún [Estilos de ventana](../../mfc/reference/window-styles.md) puede hacer una excepción de primera oportunidad que aparezca.  Esto resulta del sistema que intenta cambiar el estilo de la hoja de propiedades antes de crear la hoja.  Para evitar esta excepción, asegúrese de establecer los estilos siguientes cuando se crea `CPropertySheet`:  
  
-   DS\_3DLOOK  
  
-   DS\_CONTROL  
  
-   WS\_CHILD  
  
-   WS\_TABSTOP  
  
 Los estilos siguientes son opcionales, y no producirán excepciones de primera oportunidad:  
  
-   DS\_SHELLFONT  
  
-   DS\_LOCALEDIT  
  
-   WS\_CLIPCHILDREN  
  
 Se prohíbe cualquier otro `Window Styles` y no debe habilitarlas.  
  
 intercambiar datos entre un objeto de `CPropertySheet` y un objeto externo es similar a intercambiar datos con un objeto de `CDialog` .  La diferencia importante es que los valores de una hoja de propiedades son normalmente variables miembro de los objetos de `CPropertyPage` en lugar del propio objeto de `CPropertySheet` .  
  
 Puede crear un tipo de cuadro de diálogo de la ficha denominado un asistente, que consta de una hoja de propiedades con una secuencia de páginas de propiedades destinados a través de los pasos de una operación, como configuración de un dispositivo o crear un boletín.  En un cuadro de diálogo de la ficha del asistente\-tipo, las páginas de propiedades no tienen pestañas, y sólo una página de la propiedad es visible al mismo tiempo.  Además, en lugar de tener botones de **Aceptar** y de **Aplicar ahora** , un cuadro de diálogo de la ficha del asistente\-tipo tiene un botón de **Atrás** , botón de **Siguiente** o de **Finalizar** , botón de **Cancelar** , y un botón de **Ayuda** .  
  
 Para crear un cuadro de diálogo de asistente\-tipo, siga los mismos pasos que se usa para crear una hoja de propiedades estándar, pero la llamada [SetWizardMode](../Topic/CPropertySheet::SetWizardMode.md) antes de llamar a [DoModal](../Topic/CPropertySheet::DoModal.md).  Para habilitar los botones del asistente, llame a [SetWizardButtons](../Topic/CPropertySheet::SetWizardButtons.md), utilizando los marcadores para personalizar su función y aspecto.  Para habilitar el botón de **Finalizar** , la llamada [SetFinishText](../Topic/CPropertySheet::SetFinishText.md) después de que el usuario ha realizado medidas en la última página del asistente.  
  
 Para obtener más información sobre cómo utilizar los objetos de `CPropertySheet` , vea el artículo [hojas de propiedades y páginas de propiedades](../../mfc/property-sheets-and-property-pages-in-mfc.md).  También, vea el artículo Q146916 de Knowledge Base: HOWTO: Cree un no modal CPropertySheet con botones estándar y el caso Q300606: HOWTO: diseñar una hoja de propiedades de Resizable MFC.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPropertySheet`  
  
## Requisitos  
 **encabezado:** afxdlgs.h  
  
## Vea también  
 [ejemplo CMNCTRL1 de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo CMNCTRL2 de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo PROPDLG de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo SNAPVW de MFC](../../top/visual-cpp-samples.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)