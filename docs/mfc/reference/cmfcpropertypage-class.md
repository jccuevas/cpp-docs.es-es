---
title: Clase CMFCPropertyPage | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyPage::PreTranslateMessage method
- CMFCPropertyPage::CreateObject method
- CMFCPropertyPage class
- CMFCPropertyPage::OnSetActive method
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
caps.latest.revision: 30
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 0e9cdfa8a98c034839fac119c828cf1b92a1867a
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcpropertypage-class"></a>Clase CMFCPropertyPage
La `CMFCPropertyPage` clase admite la presentación de los menús emergentes en una página de propiedades.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCPropertyPage : public CPropertyPage  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|Construye un objeto `CMFCPropertyPage`.|  
|`CMFCPropertyPage::~CMFCPropertyPage`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCPropertyPage::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCPropertyPage::GetThisClass`|Usar el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|`CMFCPropertyPage::OnSetActive`|El marco de trabajo llama a esta función miembro cuando es elegida por el usuario de la página y se convierte en la página activa. (Invalida [notificaciones CPropertyPage:: OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).)|  
|`CMFCPropertyPage::PreTranslateMessage`|Convierte los mensajes de ventana antes de que se envíen a la [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funciones de Windows. Para obtener más información y la sintaxis del método, consulte [CWnd:: PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Invalida `CPropertyPage::PreTranslateMessage`).|  
  
## <a name="remarks"></a>Comentarios  
 La `CMFCPropertyPage` clase representa páginas individuales de una hoja de propiedades, también conocida como un cuadro de diálogo de pestaña.  
  
 Utilice la `CMFCPropertyPage` clase junto con el [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) clase. Para usar los menús en una página de propiedades, reemplace todas las apariciones de la `CPropertyPage` clase con la `CMFCPropertyPage` clase.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxpropertypage.h  
  
##  <a name="cmfcpropertypage"></a>CMFCPropertyPage::CMFCPropertyPage  
 Construye un objeto `CMFCPropertyPage`.  
  
```  
CMFCPropertyPage(
    UINT nIDTemplate,  
    UINT nIDCaption=0);

 
CMFCPropertyPage(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption=0);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDTemplate`  
 Id. de recurso de la plantilla para esta página.  
  
 `nIDCaption`  
 Id. de recurso de la etiqueta para colocar en la ficha de esta página. Si es 0, se obtiene el nombre de la plantilla de cuadro de diálogo para esta página. El valor predeterminado es 0.  
  
 `lpszTemplateName`  
 Apunta al nombre de la plantilla para esta página. No puede ser `NULL`.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de los parámetros del constructor, consulte [CPropertyPage::CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase de CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

