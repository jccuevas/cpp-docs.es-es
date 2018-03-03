---
title: Clase CMFCImageEditorPaletteBar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::GetRowHeight
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable
dev_langs:
- C++
helpviewer_keywords:
- CMFCImageEditorPaletteBar [MFC], GetRowHeight
- CMFCImageEditorPaletteBar [MFC], IsButtonExtraSizeAvailable
ms.assetid: 3fb7ba8e-f254-4d56-b913-9941b4ed8138
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 539c24acb9b58c96324bc89cdeca6c0d03c6dfdf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcimageeditorpalettebar-class"></a>Clase CMFCImageEditorPaletteBar
Proporciona la funcionalidad de la barra de paleta en un cuadro de diálogo del editor de imágenes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCImageEditorPaletteBar : public CMFCToolBar  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCImageEditorPaletteBar::GetRowHeight](#getrowheight)|Devuelve el alto de los botones de barra de herramientas. (Invalida [CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|  
|[CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|Determina si la barra de herramientas puede mostrar botones que extendió bordes. (Invalida [CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|  
  
### <a name="remarks"></a>Comentarios  
 Esta clase no está diseñada para utilizarse directamente desde el código.  
  
 El marco de trabajo utiliza esta clase para mostrar una barra de paleta en un cuadro de diálogo del editor de imágenes. Para obtener más información sobre el cuadro de diálogo del editor de imágenes, vea [CMFCImageEditorDialog clase](../../mfc/reference/cmfcimageeditordialog-class.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBa](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCImageEditorPaletteBar](../../mfc/reference/cmfcimageeditorpalettebar-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afximageeditordialog.h  
  
##  <a name="getrowheight"></a>CMFCImageEditorPaletteBar::GetRowHeight  
 Devuelve el alto de los botones de barra de herramientas.  
  
```  
virtual int GetRowHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El alto de cada botón en la barra de herramientas.  
  
##  <a name="isbuttonextrasizeavailable"></a>CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable  
 Determina si la barra de herramientas puede mostrar botones que extendió bordes.  
  
```  
virtual BOOL IsButtonExtraSizeAvailable() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Este método devuelve `FALSE`.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCImageEditorDialog (clase)](../../mfc/reference/cmfcimageeditordialog-class.md)
