---
title: Clase CMFCLinkCtrl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl::SetURL
- AFXLINKCTRL/CMFCLinkCtrl::SetURLPrefix
- AFXLINKCTRL/CMFCLinkCtrl::SizeToContent
- AFXLINKCTRL/CMFCLinkCtrl::OnDrawFocusRect
dev_langs:
- C++
helpviewer_keywords:
- CMFCLinkCtrl [MFC], SetURL
- CMFCLinkCtrl [MFC], SetURLPrefix
- CMFCLinkCtrl [MFC], SizeToContent
- CMFCLinkCtrl [MFC], OnDrawFocusRect
ms.assetid: 80f3874d-7cc8-410e-9ff1-62a225f5034b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b91bc8fec3eebba5f3037633b5840d9b1abca731
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371733"
---
# <a name="cmfclinkctrl-class"></a>Clase CMFCLinkCtrl
La `CMFCLinkCtrl` clase muestra un botón como un hipervínculo e invoca el destino del vínculo cuando se hace clic en el botón.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCLinkCtrl : public CMFCButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCLinkCtrl::SetURL](#seturl)|Muestra una dirección URL especificada como el texto del botón.|  
|[CMFCLinkCtrl::SetURLPrefix](#seturlprefix)|Establece el protocolo implícita (por ejemplo, "http:") de la dirección URL.|  
|[CMFCLinkCtrl::SizeToContent](#sizetocontent)|Cambia el tamaño del botón para que contenga el texto del botón o el mapa de bits.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|Llamado por el marco de trabajo antes de que se dibuja el rectángulo de foco del botón.|  
  
## <a name="remarks"></a>Comentarios  
 Al hacer clic en un botón que se deriva de la `CMFCLinkCtrl` (clase), el marco de trabajo pasa la dirección URL del botón como un parámetro a la `ShellExecute` método. La `ShellExecute` método abre el destino de la dirección URL.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo establecer el tamaño de un `CMFCLinkCtrl` objeto y cómo establecer una dirección url y la información sobre herramientas en un `CMFCLinkCtrl` objeto. Este ejemplo forma parte de la [ejemplo nuevos controles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#9](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#10](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxlinkctrl.h  
  
##  <a name="ondrawfocusrect"></a>  CMFCLinkCtrl::OnDrawFocusRect  
 Llamado por el marco de trabajo antes de que se dibuja el rectángulo de foco del botón.  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rectClient`  
 Un rectángulo que delimita el control de vínculo.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método si desea utilizar su propio código para dibujar el rectángulo de foco del botón.  
  
##  <a name="seturl"></a>  CMFCLinkCtrl::SetURL  
 Muestra una dirección URL especificada como el texto del botón.  
  
```  
void SetURL(LPCTSTR lpszURL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszURL`  
 El texto del botón para mostrar.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="seturlprefix"></a>  CMFCLinkCtrl::SetURLPrefix  
 Establece el protocolo implícita (por ejemplo, "http:") de la dirección URL.  
  
```  
void SetURLPrefix(LPCTSTR lpszPrefix);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszPrefix`  
 El prefijo del protocolo de dirección URL.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para establecer el prefijo de dirección URL. El prefijo no se muestra en la cara del botón, pero puede usarla para ayudar a buscar de destino de la dirección URL.  
  
##  <a name="sizetocontent"></a>  CMFCLinkCtrl::SizeToContent  
 Cambia el tamaño del botón para que contenga el texto del botón o el mapa de bits.  
  
```  
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,  
    BOOL bHCenter=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bVCenter`  
 `TRUE` Para centrar el texto del botón y mapa de bits de forma vertical entre la parte superior e inferior del control de vínculo; en caso contrario, `FALSE`. El valor predeterminado es `FALSE`.  
  
 [in] `bHCenter`  
 `TRUE` Para centrar el texto del botón y mapa de bits horizontal entre los lados izquierdo y derecho del control link; en caso contrario, `FALSE`. El valor predeterminado es `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que contiene el nuevo tamaño del control de vínculo.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CLinkCtrl](../../mfc/reference/clinkctrl-class.md)   
 [CMFCButton (clase)](../../mfc/reference/cmfcbutton-class.md)
