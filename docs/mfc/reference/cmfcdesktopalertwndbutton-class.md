---
title: Clase CMFCDesktopAlertWndButton | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCaptionButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCloseButton
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWndButton [MFC], IsCaptionButton
- CMFCDesktopAlertWndButton [MFC], IsCloseButton
ms.assetid: df39a0c8-0c39-4ab0-8c64-78c5b2c4ecaf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: efabaabdcc3f08a58cb7dc0a7845a56e5238548d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370339"
---
# <a name="cmfcdesktopalertwndbutton-class"></a>Clase CMFCDesktopAlertWndButton
Permite botones que deben agregarse a un cuadro de diálogo de alerta de escritorio.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCDesktopAlertWndButton : public CMFCButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|Constructor predeterminado.|  
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|Determina si el botón se muestra en el área de título del cuadro de diálogo de alerta.|  
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|Determina si el botón cierra el cuadro de diálogo de alerta.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|nombre|Descripción|  
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|Un valor booleano que especifica si el botón se muestra en el área de título del cuadro de diálogo de alerta.|  
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|Un valor booleano que especifica si el botón cierra el cuadro de diálogo de alerta.|  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el constructor establece la `m_bIsCaptionButton` y `m_bIsCloseButton` los miembros de datos `FALSE`. El elemento primario `CMFCDesktopAlertDialog` conjuntos de objetos `m_bIsCaptionButton` a `TRUE` si el botón está situado en el área de título del cuadro de diálogo de alerta. El `CMFCDesktopAlertDialog` clase crea un `CMFCDesktopAlertWndButton` objeto que actúa como el botón que se cierra el cuadro de diálogo Alerta cuadro y establece `m_bIsCloseButton` a `TRUE`.  
  
 Agregar `CMFCDesktopAlertWndButton` objetos a un `CMFCDesktopAlertDialog` como lo haría cualquier botón del objeto. Para obtener más información acerca de `CMFCDesktopAlertDialog`, consulte [CMFCDesktopAlertDialog clase](../../mfc/reference/cmfcdesktopalertdialog-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `SetImage` método en la `CMFCDesktopAlertWndButton` clase. Este fragmento de código forma parte de la [ejemplo de demostración de alerta de escritorio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]  
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdesktopalertwnd.h  
  
##  <a name="iscaptionbutton"></a>  CMFCDesktopAlertWndButton::IsCaptionButton  
 Determina si el botón se muestra en el área de título del cuadro de diálogo de alerta.  
  
```  
BOOL IsCaptionButton() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el botón se muestra en el área de título del cuadro de diálogo alertas; en caso contrario, es 0.  
  
##  <a name="isclosebutton"></a>  CMFCDesktopAlertWndButton::IsCloseButton  
 Determina si el botón cierra el cuadro de diálogo de alerta.  
  
```  
BOOL IsCloseButton() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el botón cierra el cuadro de diálogo alertas; en caso contrario, es 0.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertDialog (clase)](../../mfc/reference/cmfcdesktopalertdialog-class.md)
