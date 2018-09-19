---
title: CMFCRibbonCustomizeDialog (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCustomizeDialog [MFC], CMFCRibbonCustomizeDialog
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d342ec75fd45224dcd36ba3fc17aa1a6f8c12e33
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720660"
---
# <a name="cmfcribboncustomizedialog-class"></a>CMFCRibbonCustomizeDialog (clase)
Muestra la cinta de opciones **personalizar** página.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog](#cmfcribboncustomizedialog)|Construye un objeto `CMFCRibbonCustomizeDialog`.|  
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCRibbonCustomizeDialog::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|  
  
## <a name="remarks"></a>Comentarios  
 MFC crea instancias de esta clase automáticamente si no procesar el mensaje AFX_WM_ON_RIBBON_CUSTOMIZE, o si se devuelve 0 desde el controlador de mensajes.  
  
 Si desea utilizar esta clase en la aplicación para mostrar la cinta de opciones **personalizar** diálogo cuadro, simplemente crear instancias del mismo y llamar a la `DoModal` método.  
  
 Dado que esta clase se deriva [CMFCPropertySheet (clase)](../../mfc/reference/cmfcpropertysheet-class.md), puede agregar páginas personalizadas mediante el `CMFCPropertySheet` API.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)  
  
 [CMFCRibbonCustomizeDialog](../../mfc/reference/cmfcribboncustomizedialog-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxribboncustomizedialog.h  
  
##  <a name="cmfcribboncustomizedialog"></a>  CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog  
 Construye un objeto `CMFCRibbonCustomizeDialog`.  
  
```  
CMFCRibbonCustomizeDialog(
    CWnd* pWndParent,  
    CMFCRibbonBar* pRibbon);
```  
  
### <a name="parameters"></a>Parámetros  
*pWndParent*<br/>
[in] Un puntero a la ventana primaria (normalmente, el marco principal).  
  
*pRibbon*<br/>
[in] Un puntero a la `CMFCRibbonBar` que consiste en Personalizar.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un `CMFCRibbonCustomizeDialog` objeto.  
  
 [!code-cpp[NVC_MFC_RibbonApp#18](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]  
  
### <a name="remarks"></a>Comentarios  
 El constructor crea un [CMFCRibbonCustomizePropertyPage (clase)](../../mfc/reference/cmfcribboncustomizepropertypage-class.md) objeto y lo agrega a la colección de páginas de propiedades.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)
