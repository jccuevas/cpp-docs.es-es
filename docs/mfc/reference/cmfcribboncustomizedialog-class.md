---
title: Clase CMFCRibbonCustomizeDialog | Documentos de Microsoft
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
ms.openlocfilehash: d195b2888c47a318369df13c371f85b21cc7bf84
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370199"
---
# <a name="cmfcribboncustomizedialog-class"></a>Clase CMFCRibbonCustomizeDialog
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
|`CMFCRibbonCustomizeDialog::GetThisClass`|Usado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
  
## <a name="remarks"></a>Comentarios  
 MFC crea instancias de esta clase automáticamente si no procesar el mensaje AFX_WM_ON_RIBBON_CUSTOMIZE, o si se devuelve 0 desde el controlador de mensajes.  
  
 Si desea utilizar esta clase en la aplicación para mostrar la cinta de opciones **personalizar** diálogo cuadro, simplemente crear instancias de él y llame a la `DoModal` método.  
  
 Dado que esta clase se deriva de [CMFCPropertySheet clase](../../mfc/reference/cmfcpropertysheet-class.md), puede agregar páginas personalizadas mediante la `CMFCPropertySheet` API.  
  
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
 [in] `pWndParent`  
 Un puntero a la ventana primaria (normalmente, el marco principal).  
  
 [in] `pRibbon`  
 Un puntero a la `CMFCRibbonBar` que va a personalizar.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un `CMFCRibbonCustomizeDialog` objeto.  
  
 [!code-cpp[NVC_MFC_RibbonApp#18](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]  
  
### <a name="remarks"></a>Comentarios  
 El constructor crea un [CMFCRibbonCustomizePropertyPage clase](../../mfc/reference/cmfcribboncustomizepropertypage-class.md) y la agrega a la colección de páginas de la hoja de propiedades.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)
