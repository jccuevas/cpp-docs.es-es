---
title: Clase CMFCStandardColorsPropertyPage | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CMFCStandardColorsPropertyPage class [MFC]
ms.assetid: b84b7cfb-bb24-4c65-804a-5b642cb64400
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: abaad4870354ba331e615e0739dc7526dd39607d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcstandardcolorspropertypage-class"></a>Clase CMFCStandardColorsPropertyPage
Representa una página de propiedades que los usuarios usan para seleccionar colores estándar en un cuadro de diálogo color.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCStandardColorsPropertyPage : public CPropertyPage  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CMFCStandardColorsPropertyPage::CMFCStandardColorsPropertyPage`|Constructor predeterminado.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CMFCStandardColorsPropertyPage::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCStandardColorsPropertyPage::GetThisClass`|Usado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
  
### <a name="remarks"></a>Comentarios  
 La `CMFCColorDialog` clase utiliza esta clase para mostrar la página de propiedades de color estándar. Para obtener más información acerca de `CMFCColorDialog`, consulte [CMFCColorDialog clase](../../mfc/reference/cmfccolordialog-class.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCStandardColorsPropertyPage](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxstandardcolorspropertypage.h  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)   
 [CMFCCustomColorsPropertyPage (clase)](../../mfc/reference/cmfccustomcolorspropertypage-class.md)
