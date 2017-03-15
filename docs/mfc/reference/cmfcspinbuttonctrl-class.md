---
title: Clase CMFCSpinButtonCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCSpinButtonCtrl
dev_langs:
- C++
helpviewer_keywords:
- CMFCSpinButtonCtrl class
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
caps.latest.revision: 25
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: c1832062461f2ed53df07a72428089179ed493ab
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcspinbuttonctrl-class"></a>Clase CMFCSpinButtonCtrl
La `CMFCSpinButtonCtrl` clase admite un administrador visual que dibuja un control de botón de número.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCSpinButtonCtrl : public CSpinButtonCtrl  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|Constructor predeterminado.|  
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCSpinButtonCtrl::OnDraw](#ondraw)|Vuelve a dibujar el control de botón de número actual.|  
  
## <a name="remarks"></a>Comentarios  
 Para usar un administrador visual para dibujar un control de botón de número en la aplicación, reemplace todas las instancias de la `CSpinButtonCtrl` clase con la `CMFCSpinButtonCtrl` clase.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo crear un objeto de la `CMFCSpinButtonCtrl` clase y usar su `Create` método.  
  
 [!code-cpp[NVC_MFC_RibbonApp&#25;](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)  
  
 [CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxspinbuttonctrl.h  
  
##  <a name="a-nameondrawa--cmfcspinbuttonctrlondraw"></a><a name="ondraw"></a>CMFCSpinButtonCtrl::OnDraw  
 Vuelve a dibujar el control de botón de número actual.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
### <a name="remarks"></a>Comentarios  
 El marco llama el `CMFCSpinButtonCtrl::OnPaint` método para controlar la [CWnd::OnPaint](../../mfc/reference/cwnd-class.md#onpaint) mensaje y que a su vez llama método esto `CMFCSpinButtonCtrl::OnDraw` (método). Invalide este método para personalizar la forma en que el marco dibuja el control de botón de número.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)

