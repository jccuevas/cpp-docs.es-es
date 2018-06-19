---
title: Clase CMFCCustomColorsPropertyPage | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage::Setup
dev_langs:
- C++
helpviewer_keywords:
- CMFCCustomColorsPropertyPage [MFC], Setup
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c02c2590e4143460a2cd89bb2b7e7e167c92c0e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370814"
---
# <a name="cmfccustomcolorspropertypage-class"></a>Clase CMFCCustomColorsPropertyPage
Representa una página de propiedades que puede seleccionar colores personalizados en un cuadro de diálogo color.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCCustomColorsPropertyPage : public CPropertyPage  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|Constructor predeterminado.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CMFCCustomColorsPropertyPage::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCCustomColorsPropertyPage::GetThisClass`|Usado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMFCCustomColorsPropertyPage::Setup](#setup)|Establece los componentes de color de la página de propiedades.|  
  
### <a name="remarks"></a>Comentarios  
 La `CMFCColorDialog` clase utiliza esta clase para mostrar la página de propiedades de color personalizado. Para obtener más información acerca de `CMFCColorDialog`, consulte [CMFCColorDialog clase](../../mfc/reference/cmfccolordialog-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un `CMFCCustomColorsPropertyPage` de objeto y establecer los componentes de color de la página de propiedades.  
  
 [!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcustomcolorspropertypage.h  
  
##  <a name="setup"></a>  CMFCCustomColorsPropertyPage::Setup  
 Establece los componentes de color de la página de propiedades.  
  
```  
void Setup(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `R`|El componente rojo del valor RGB.|  
|[in] `G`|El componente verde del valor RGB.|  
|[in] `B`|El componente azul del valor RGB.|  
  
### <a name="remarks"></a>Comentarios  
 Este método actualiza el RGB actual y los asociados HLS (matiz, luminosidad y saturación) valores de color de la página de propiedades. El [CMFCColorDialog::SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo) método llama a este método cuando el marco de trabajo inicializa el cuadro de diálogo color o el usuario presiona el botón primario del mouse. Para obtener más información acerca de `CMFCColorDialog`, consulte [CMFCColorDialog clase](../../mfc/reference/cmfccolordialog-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)   
 [CMFCStandardColorsPropertyPage (clase)](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
