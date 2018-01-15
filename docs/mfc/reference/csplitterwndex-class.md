---
title: Clase CSplitterWndEx | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
dev_langs: C++
helpviewer_keywords: CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 94ec633718dda81a5183a59eb46387b361d0f004
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="csplitterwndex-class"></a>Clase CSplitterWndEx



Representa una ventana divisora personalizada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CSplitterWndEx : public CSplitterWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CSplitterWndEx::CSplitterWndEx`|Constructor predeterminado.|  
|`CSplitterWndEx::~CSplitterWndEx`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|Lo llama el marco de trabajo para dibujar una ventana divisora. (Invalida [CSplitterWnd::OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter).)|  
  
## <a name="remarks"></a>Comentarios  
 Invalidar el `OnDrawSplitter` método para personalizar la apariencia de los componentes gráficos de una ventana divisora.  
  
 El `CSplitterWndEx` clase se utiliza junto con la [OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder), [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox), y [OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground) métodos, que son se implementa mediante un administrador visual. Para hacer que un administrador visual dibujar una ventana divisora en la aplicación, reemplace las declaraciones de la `CSplitterWnd` clase con la `CSplitterWndEx` clase. Para las aplicaciones de la ventana de marco, se declara la clase de ventana divisora en la clase CMainFrame que se encuentra en mainfrm.h. Para obtener un ejemplo, vea el `OutlookDemo` en el directorio de ejemplos.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](cobject-class.md)  
  
 [CCmdTarget](ccmdtarget-class.md)  
  
 [CWnd](cwnd-class.md)  
  
 [CSplitterWnd](csplitterwnd-class.md)  
   
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxsplitterwndex.h  
  
##  <a name="ondrawsplitter"></a>CSplitterWndEx::OnDrawSplitter  
 Lo llama el marco de trabajo para dibujar una ventana divisora.  
  
```  
virtual void OnDrawSplitter(  
   CDC* pDC,  
   ESplitType nType,  
   const CRect& rect   
);  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero al contexto de dispositivo. Si este parámetro es `NULL`, el marco de trabajo se vuelve a dibujar la ventana activa.  
  
 [in] `nType`  
 Uno de los `CSplitterWnd::ESplitType` valores de enumeración que especifica el elemento de ventana divisora para dibujar. Los valores válidos son `splitBox`, `splitBar`, `splitIntersection` y `splitBorder`.  
  
 [in] `rect`  
 Un rectángulo delimitador que especifica las dimensiones y la ubicación para dibujar el elemento de ventana de separación especificada.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../hierarchy-chart.md)   
 [Clases](mfc-classes.md)   
 [CSplitterWnd (clase)](csplitterwnd-class.md)   
 [CMFCVisualManager (clase)](cmfcvisualmanager-class.md)