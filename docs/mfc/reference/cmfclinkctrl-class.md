---
title: Clase CMFCLinkCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCLinkCtrl
dev_langs:
- C++
helpviewer_keywords:
- CMFCLinkCtrl class
ms.assetid: 80f3874d-7cc8-410e-9ff1-62a225f5034b
caps.latest.revision: 27
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
ms.openlocfilehash: 8c926c0ef611470b137d2bb897c012a85645c90c
ms.lasthandoff: 02/24/2017

---
# <a name="cmfclinkctrl-class"></a>Clase CMFCLinkCtrl
La `CMFCLinkCtrl` clase muestra un botón como hipervínculo e invoca el destino del vínculo cuando se hace clic en el botón.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCLinkCtrl : public CMFCButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCLinkCtrl::SetURL](#seturl)|Muestra una dirección URL especificada como el texto del botón.|  
|[CMFCLinkCtrl::SetURLPrefix](#seturlprefix)|Establece el protocolo implícito (por ejemplo, "http:") de la dirección URL.|  
|[CMFCLinkCtrl::SizeToContent](#sizetocontent)|Cambia el tamaño del botón para que contenga el texto del botón o el mapa de bits.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|Llamado por el marco de trabajo antes de que se dibuja el rectángulo de foco del botón.|  
  
## <a name="remarks"></a>Comentarios  
 Al hacer clic en un botón que se deriva de la `CMFCLinkCtrl` (clase), el marco de trabajo pasa la dirección URL del botón como un parámetro a la `ShellExecute` (método). La `ShellExecute` método abre el destino de la dirección URL.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo establecer el tamaño de una `CMFCLinkCtrl` objeto y cómo establecer una dirección url y la información sobre herramientas en un `CMFCLinkCtrl` objeto. Este ejemplo forma parte de la [ejemplo nuevos controles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls&#9;](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls&#10;](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxlinkctrl.h  
  
##  <a name="a-nameondrawfocusrecta--cmfclinkctrlondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFCLinkCtrl::OnDrawFocusRect  
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
  
##  <a name="a-nameseturla--cmfclinkctrlseturl"></a><a name="seturl"></a>CMFCLinkCtrl::SetURL  
 Muestra una dirección URL especificada como el texto del botón.  
  
```  
void SetURL(LPCTSTR lpszURL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszURL`  
 Para mostrar el texto del botón.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameseturlprefixa--cmfclinkctrlseturlprefix"></a><a name="seturlprefix"></a>CMFCLinkCtrl::SetURLPrefix  
 Establece el protocolo implícito (por ejemplo, "http:") de la dirección URL.  
  
```  
void SetURLPrefix(LPCTSTR lpszPrefix);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszPrefix`  
 El prefijo del protocolo de dirección URL.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para establecer el prefijo de dirección URL. El prefijo no aparece en la cara del botón, pero puede utilizar para buscar de destino la dirección de URL.  
  
##  <a name="a-namesizetocontenta--cmfclinkctrlsizetocontent"></a><a name="sizetocontent"></a>CMFCLinkCtrl::SizeToContent  
 Cambia el tamaño del botón para que contenga el texto del botón o el mapa de bits.  
  
```  
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,  
    BOOL bHCenter=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bVCenter`  
 `TRUE`Para centrar el texto del botón y el mapa de bits verticalmente entre la parte superior e inferior del control de vínculo; de lo contrario, `FALSE`. El valor predeterminado es `FALSE`.  
  
 [in] `bHCenter`  
 `TRUE`Para centrar el texto del botón y el mapa de bits horizontal entre los lados izquierdo y derecho del control de vínculo; de lo contrario, `FALSE`. El valor predeterminado es `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que contiene el nuevo tamaño del control de vínculo.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CLinkCtrl](../../mfc/reference/clinkctrl-class.md)   
 [Clase CMFCButton](../../mfc/reference/cmfcbutton-class.md)

