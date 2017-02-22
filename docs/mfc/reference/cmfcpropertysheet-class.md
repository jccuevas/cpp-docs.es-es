---
title: "CMFCPropertySheet Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCPropertySheet"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPropertySheet class"
  - "CMFCPropertySheet::OnInitDialog method"
  - "CMFCPropertySheet::PreTranslateMessage method"
ms.assetid: 01d93573-9698-440f-a6a4-5bebbee879dc
caps.latest.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 37
---
# CMFCPropertySheet Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase `CMFCPropertySheet` admite una hoja de propiedades donde cada página de propiedades se indica mediante una pestaña de página, un botón de barra de herramientas, un nodo del control de árbol o un elemento de lista.  
  
## Sintaxis  
  
```  
class CMFCPropertySheet : public CPropertySheet  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPropertySheet::CMFCPropertySheet](../Topic/CMFCPropertySheet::CMFCPropertySheet.md)|Construye un objeto `CMFCPropertySheet`.|  
|`CMFCPropertySheet::~CMFCPropertySheet`|Destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPropertySheet::AddPage](../Topic/CMFCPropertySheet::AddPage.md)|Agrega una página a la hoja de propiedades.|  
|[CMFCPropertySheet::AddPageToTree](../Topic/CMFCPropertySheet::AddPageToTree.md)|Agrega una nueva página de propiedades al control de árbol.|  
|[CMFCPropertySheet::AddTreeCategory](../Topic/CMFCPropertySheet::AddTreeCategory.md)|Agrega un nuevo nodo al control de árbol.|  
|[CMFCPropertySheet::EnablePageHeader](../Topic/CMFCPropertySheet::EnablePageHeader.md)|Reserva espacio en la parte superior de cada página para dibujar un encabezado personalizado.|  
|[CMFCPropertySheet::GetHeaderHeight](../Topic/CMFCPropertySheet::GetHeaderHeight.md)|Recupera el alto del encabezado actual.|  
|[CMFCPropertySheet::GetLook](../Topic/CMFCPropertySheet::GetLook.md)|Recupera un valor de enumeración que especifica el aspecto de la hoja de propiedades actual.|  
|[CMFCPropertySheet::GetNavBarWidth](../Topic/CMFCPropertySheet::GetNavBarWidth.md)|Recupera el ancho de la barra de navegación, en píxeles.|  
|[CMFCPropertySheet::GetTab](../Topic/CMFCPropertySheet::GetTab.md)|Recupera el objeto de control de la pestaña interna que admite el control de la hoja de propiedades actual.|  
|`CMFCPropertySheet::GetThisClass`|Lo usa el marco de trabajo para obtener un puntero al objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|[CMFCPropertySheet::InitNavigationControl](../Topic/CMFCPropertySheet::InitNavigationControl.md)|Inicializa el aspecto del control de la hoja de propiedades actual.|  
|[CMFCPropertySheet::OnActivatePage](../Topic/CMFCPropertySheet::OnActivatePage.md)|Lo llama el marco de trabajo cuando se ha habilitado una página de propiedades.|  
|[CMFCPropertySheet::OnDrawPageHeader](../Topic/CMFCPropertySheet::OnDrawPageHeader.md)|Lo llama el marco de trabajo para dibujar un encabezado de la página de propiedades personalizada.|  
|`CMFCPropertySheet::OnInitDialog`|Controla el mensaje [WM\_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428).  \(Invalida [CPropertySheet::OnInitDialog](../Topic/CPropertySheet::OnInitDialog.md)\).|  
|[CMFCPropertySheet::OnRemoveTreePage](../Topic/CMFCPropertySheet::OnRemoveTreePage.md)|Lo llama el marco de trabajo para quitar una página de propiedades de un control de árbol.|  
|`CMFCPropertySheet::PreTranslateMessage`|Traduce los mensajes de ventana antes de enviarlos a las funciones de Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934).  \(Invalida `CPropertySheet::PreTranslateMessage`\).|  
|[CMFCPropertySheet::RemoveCategory](../Topic/CMFCPropertySheet::RemoveCategory.md)|Quita un nodo del control de árbol.|  
|[CMFCPropertySheet::RemovePage](../Topic/CMFCPropertySheet::RemovePage.md)|Quita una página de propiedades de la hoja de propiedades.|  
|[CMFCPropertySheet::SetIconsList](../Topic/CMFCPropertySheet::SetIconsList.md)|Especifica la lista de imágenes que se usan en el control de navegación del panel de Outlook.|  
|[CMFCPropertySheet::SetLook](../Topic/CMFCPropertySheet::SetLook.md)|Especifica el aspecto de la hoja de propiedades.|  
  
## Comentarios  
 La clase `CMFCPropertySheet` representa hojas de propiedades, también conocidas como cuadros de diálogo de pestaña.  La clase `CMFCPropertySheet` puede mostrar una página de propiedades de varias formas.  
  
 Realice los pasos siguientes para usar la clase `CMFCPropertySheet` en la aplicación:  
  
1.  Derive una clase de la clase `CMFCPropertySheet` y llámela, por ejemplo, CMyPropertySheet.  
  
2.  Construya un objeto [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md) para cada página de propiedades.  
  
3.  Llame al método [CMFCPropertySheet::SetLook](../Topic/CMFCPropertySheet::SetLook.md) del constructor CMyPropertySheet.  Un parámetro de ese método especifica que las páginas de propiedades se mostrarán como pestañas a lo largo de la parte superior o izquierda de la hoja de propiedades, como pestañas en el estilo de una hoja de propiedades de Microsoft OneNote, como botones en un control de barra de herramientas de Microsoft Outlook, como nodos en un control de árbol o como una lista de elementos en el lado izquierdo de la hoja de propiedades.  
  
4.  Si crea una hoja de propiedades en el estilo de una barra de herramientas de Microsoft Outlook, llame al método [CMFCPropertySheet::SetIconsList](../Topic/CMFCPropertySheet::SetIconsList.md) para asociar una lista de imágenes junto con las páginas de propiedades.  
  
5.  Llame al método [CMFCPropertySheet::AddPage](../Topic/CMFCPropertySheet::AddPage.md) para cada página de propiedades.  
  
6.  Cree un control `CMFCPropertySheet` y llame a su método `DoModal`.  
  
## Ilustraciones  
 La siguiente ilustración muestra una hoja de propiedades que se encuentra en el estilo de una barra de herramientas incrustada de Microsoft Outlook.  La barra de herramientas de Outlook aparece en el lado izquierdo de la hoja de propiedades.  
  
 ![Controles de color de CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_color.png "cmfcpropertysheet\_color")  
  
 La siguiente ilustración muestra una hoja de propiedades que contiene un objeto [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md).  Ese objeto es una hoja de propiedades del estilo de una hoja de propiedades de controles comunes estándar.  
  
 ![Controles de propiedad y lista de CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_list.png "cmfcpropertysheet\_list")  
  
 La siguiente ilustración muestra una hoja de propiedades que se encuentra en el estilo de un control de árbol.  
  
 ![Árbol de propiedades](../../mfc/reference/media/proptree.png "PropTree")  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)  
  
## Requisitos  
 **Encabezado:** afxpropertysheet.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyPage Class](../../mfc/reference/cmfcpropertypage-class.md)   
 [CMFCOutlookBar \(Clase\)](../../mfc/reference/cmfcoutlookbar-class.md)