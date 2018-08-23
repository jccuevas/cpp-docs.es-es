---
title: CMFCDragFrameImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDragFrameImpl
dev_langs:
- C++
helpviewer_keywords:
- CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aee2c58d8763581987fec40b0cb486c67363697b
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540883"
---
# <a name="cmfcdragframeimpl-class"></a>CMFCDragFrameImpl (clase)
La `CMFCDragFrameImpl` clase dibuja el rectángulo de arrastre que aparece cuando el usuario arrastra un panel en modo de acoplamiento estándar.  
   Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.  
   
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCDragFrameImpl  
```  
  
## <a name="remarks"></a>Comentarios  
 Un objeto de esta clase está incrustado en cada [clase CPane](../../mfc/reference/cpane-class.md) objeto. Por lo tanto, cada panel que usa el `CanFloat` método muestra un rectángulo de arrastre cuando el usuario lo arrastra.  
  
 Puede controlar el grosor del rectángulo de arrastre mediante [AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](afx-global-data-structure.md#m_ndragframethicknessfloat) y [AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdragframeimpl.h  
  
##  <a name="enddrawdragframe"></a>  CMFCDragFrameImpl::EndDrawDragFrame  

  
```  
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bClearInternalRects*  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="init"></a>  CMFCDragFrameImpl::Init  

  
```  
void Init(CWnd* pDraggedWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDraggedWnd*  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="movedragframe"></a>  CMFCDragFrameImpl::MoveDragFrame  

  
```  
void MoveDragFrame(BOOL bForceMove = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bForceMove*  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="placetabpredocking"></a>  CMFCDragFrameImpl::PlaceTabPreDocking  

  
```  
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,  
    BOOL bFirstTime);  
  
void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pTabbedBar*  
 [in] *bFirstTime*  
 [in] *pCBarToPlaceOn*  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="removetabpredocking"></a>  CMFCDragFrameImpl::RemoveTabPreDocking  

  
```  
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pOldTargetBar*  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="resetstate"></a>  CMFCDragFrameImpl::ResetState  

  
```  
void ResetState();
```  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CPane (clase)](../../mfc/reference/cpane-class.md)