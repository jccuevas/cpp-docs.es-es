---
title: Clase CMFCRibbonMainPanel | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::Add
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddRecentFilesList
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToBottom
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToRight
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::GetCommandsFrame
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonMainPanel class
ms.assetid: 1af78798-5e75-4365-9c81-a54aa5679602
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 3fc37a953e62e6ea90de8402b7f2912b06967e13
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonmainpanel-class"></a>Clase CMFCRibbonMainPanel
Implementa un panel de cinta de opciones que se muestra al hacer clic en el [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonMainPanel : public CMFCRibbonPanel  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|Constructor predeterminado.|  
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonMainPanel::Add](#add)|Agrega un elemento de la cinta de opciones en el panel izquierdo del panel de botones de la aplicación. (Invalida [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).)|  
|[CMFCRibbonMainPanel::AddRecentFilesList](#addrecentfileslist)|Agrega una cadena de texto en el menú de lista de archivos recientes.|  
|[CMFCRibbonMainPanel::AddToBottom](#addtobottom)|Agrega un elemento de la cinta de opciones en el panel inferior del panel de la aplicación de cinta.|  
|[CMFCRibbonMainPanel::AddToRight](#addtoright)|Agrega un elemento de la cinta de opciones en el panel derecho del panel de botones de la aplicación.|  
|`CMFCRibbonMainPanel::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCRibbonMainPanel::GetCommandsFrame](#getcommandsframe)|Devuelve un rectángulo que representa el área del panel principal de la cinta.|  
|`CMFCRibbonMainPanel::GetThisClass`|Usar el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
  
## <a name="remarks"></a>Comentarios  
 El marco de trabajo muestra el `CMFCRibbonMainPanel` al abrir el panel de la aplicación. Contiene tres paneles:  
  
-   El panel izquierdo contiene comandos asociados con los archivos, como **abiertos**, **guardar**, **imprimir**, y **cerrar**. Para agregar un comando a este panel, llame a [CMFCRibbonMainPanel::Add](#add).  
  
-   El panel derecho contiene opciones que modifican el comando que se hace clic en el panel izquierdo. Por ejemplo, si hace clic en **Guardar como** en el panel izquierdo, el panel derecho puede mostrar tipos de archivo disponibles. Para agregar un elemento a este panel, llame a [CMFCRibbonMainPanel::AddToRight](#addtoright).  
  
-   El panel inferior contiene botones que le permiten cambiar la configuración de la aplicación y salir del programa. Para agregar un elemento a este panel, llame a [CMFCRibbonMainPanel::AddToBottom](#addtobottom).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)  
  
 [CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxRibbonMainPanel.h  
  
##  <a name="add"></a>CMFCRibbonMainPanel::Add  
 Agrega un elemento de la cinta de opciones en el panel izquierdo del panel de botones de la aplicación.  
  
```  
virtual void Add(CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out]`pElem`  
 Un puntero al elemento de cinta de opciones para agregar al panel principal.  
  
### <a name="remarks"></a>Comentarios  
 Agrega un elemento de la cinta de opciones en el panel. Los elementos agregados con este método se encuentra en la columna izquierda del panel principal.  
  
##  <a name="addrecentfileslist"></a>CMFCRibbonMainPanel::AddRecentFilesList  
 Agrega una cadena de texto en el menú de lista de archivos recientes.  
  
```  
void AddRecentFilesList(
    LPCTSTR lpszLabel,  
    int nWidth = 300);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszLabel`  
 Especifica la cadena que se agregará a la lista de archivos recientes.  
  
 `nWidth`  
 Especifica el ancho, en píxeles, del panel de lista de archivos recientes.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="addtobottom"></a>CMFCRibbonMainPanel::AddToBottom  
 Agrega un elemento de la cinta de opciones en el panel inferior del panel de la aplicación de cinta.  
  
```  
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out]`pElem`  
 Un puntero al elemento de cinta de opciones para agregar a la parte inferior del panel principal.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="addtoright"></a>CMFCRibbonMainPanel::AddToRight  
 Agrega un elemento de la cinta de opciones en el panel derecho del panel de botones de la aplicación.  
  
```  
void AddToRight(
    CMFCRibbonBaseElement* pElem,  
    int nWidth = 300);
```  
  
### <a name="parameters"></a>Parámetros  
 `pElem`  
 Puntero a un elemento de cinta que se agregarán a la derecha del panel principal.  
  
 `nWidth`  
 Especifica el ancho, en píxeles, del panel derecho.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para agregar un elemento de la cinta de opciones en el panel derecho. Normalmente, el panel derecho muestra la lista de archivos recientes, pero puede agregar aquí cualquier otro elemento de cinta de opciones.  
  
##  <a name="getcommandsframe"></a>CMFCRibbonMainPanel::GetCommandsFrame  
 Devuelve un rectángulo que representa el área del panel principal de la cinta.  
  
```  
CRect GetCommandsFrame() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un rectángulo que representa el área del panel principal de la cinta.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)

