---
title: Clase CMFCSpinButtonCtrl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl::OnDraw
dev_langs:
- C++
helpviewer_keywords:
- CMFCSpinButtonCtrl [MFC], OnDraw
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b8c602882036d77105bb619069a6e43d73ceeb6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcspinbuttonctrl-class"></a>Clase CMFCSpinButtonCtrl
La `CMFCSpinButtonCtrl` clase es compatible con un administrador visual que dibuja un control de botón de número.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCSpinButtonCtrl : public CSpinButtonCtrl  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|Constructor predeterminado.|  
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCSpinButtonCtrl::OnDraw](#ondraw)|Vuelve a dibujar el control de botón de número actual.|  
  
## <a name="remarks"></a>Comentarios  
 Para utilizar un administrador visual para dibujar un control de botón de número en la aplicación, reemplace todas las instancias de la `CSpinButtonCtrl` clase con la `CMFCSpinButtonCtrl` clase.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo crear un objeto de la `CMFCSpinButtonCtrl` clase y usar su `Create` método.  
  
 [!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)  
  
 [CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxspinbuttonctrl.h  
  
##  <a name="ondraw"></a>  CMFCSpinButtonCtrl::OnDraw  
 Vuelve a dibujar el control de botón de número actual.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
### <a name="remarks"></a>Comentarios  
 Las llamadas de framework la `CMFCSpinButtonCtrl::OnPaint` método para controlar la [CWnd::OnPaint](../../mfc/reference/cwnd-class.md#onpaint) mensaje, y que a su vez llamadas de método esto `CMFCSpinButtonCtrl::OnDraw` método. Invalide este método para personalizar la forma en que el marco de trabajo dibuja el control de botón de número.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager (clase)](../../mfc/reference/cmfcvisualmanager-class.md)
