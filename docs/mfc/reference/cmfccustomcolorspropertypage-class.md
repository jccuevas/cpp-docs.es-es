---
title: CMFCCustomColorsPropertyPage (clase) | Microsoft Docs
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
ms.openlocfilehash: 6c8fea125c61bebe836a31c0b2718741e8c531d3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716872"
---
# <a name="cmfccustomcolorspropertypage-class"></a>CMFCCustomColorsPropertyPage (clase)
Representa una página de propiedades que puede seleccionar los colores personalizados en un cuadro de diálogo color.  
  
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
|`CMFCCustomColorsPropertyPage::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|  
|[CMFCCustomColorsPropertyPage::Setup](#setup)|Establece los componentes de color de la página de propiedades.|  
  
### <a name="remarks"></a>Comentarios  
 El `CMFCColorDialog` usa esta clase para mostrar la página de propiedades de color personalizado. Para obtener más información acerca de `CMFCColorDialog`, consulte [CMFCColorDialog (clase)](../../mfc/reference/cmfccolordialog-class.md).  
  
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
|*R*|[in] El componente rojo del valor RGB.|  
|*G*|[in] El componente verde del valor RGB.|  
|*B*|[in] El componente azul del valor RGB.|  
  
### <a name="remarks"></a>Comentarios  
 Este método actualiza el RGB actual y los asociados HLS (matiz, saturación y luminosidad) valores de color de la página de propiedades. El [CMFCColorDialog::SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo) método llama a este método cuando el marco de trabajo inicializa el cuadro de diálogo color o el usuario presiona el botón primario del mouse. Para obtener más información acerca de `CMFCColorDialog`, consulte [CMFCColorDialog (clase)](../../mfc/reference/cmfccolordialog-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCColorDialog (clase)](../../mfc/reference/cmfccolordialog-class.md)   
 [CMFCStandardColorsPropertyPage (clase)](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
