---
title: Clase CSplitterWndEx | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
dev_langs:
- C++
helpviewer_keywords:
- CSplitterWndEx
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
caps.latest.revision: 24
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
ms.sourcegitcommit: 73410ae17465880f455e5b15026f6cc010803c19
ms.openlocfilehash: 08b26bc2321485181941dbaaa9a903de9a401ef8
ms.lasthandoff: 02/24/2017

---
# <a name="csplitterwndex-class"></a>Clase CSplitterWndEx



Representa una ventana divisora personalizada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CSplitterWndEx : public CSplitterWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CSplitterWndEx::CSplitterWndEx`|Constructor predeterminado.|  
|`CSplitterWndEx::~CSplitterWndEx`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|Llamado por el marco para dibujar una ventana divisora. (Invalida [CSplitterWnd::OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter).)|  
  
## <a name="remarks"></a>Comentarios  
 Invalidar el `OnDrawSplitter` método para personalizar la apariencia de los componentes gráficos de una ventana divisora.  
  
 El `CSplitterWndEx` clase se utiliza junto con el [OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder), [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox), y [OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground) métodos, que se implementan mediante un administrador visual. Para hacer que un administrador visual dibujar una ventana divisora en la aplicación, sustituir las declaraciones de la `CSplitterWnd` clase con la `CSplitterWndEx` clase. Para las aplicaciones de la ventana de marco, se declara la clase de ventana divisora en la clase CMainFrame que se encuentra en mainfrm.h. Para obtener un ejemplo, consulte el `OutlookDemo` en el directorio de ejemplos.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](cobject-class.md)  
  
 [CCmdTarget](ccmdtarget-class.md)  
  
 [CWnd](cwnd-class.md)  
  
 [CSplitterWnd](csplitterwnd-class.md)  
   
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxsplitterwndex.h  
  
##  <a name="ondrawsplitter"></a>CSplitterWndEx::OnDrawSplitter  
 Llamado por el marco para dibujar una ventana divisora.  
  
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
 Uno de los `CSplitterWnd::ESplitType` los valores de enumeración que especifica el elemento de la ventana divisora para dibujar. Los valores válidos son `splitBox`, `splitBar`, `splitIntersection` y `splitBorder`.  
  
 [in] `rect`  
 Un rectángulo delimitador que especifica las dimensiones y ubicación para dibujar el elemento de la ventana divisora especificado.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../hierarchy-chart.md)   
 [Clases](mfc-classes.md)   
 [CSplitterWnd (clase)](csplitterwnd-class.md)   
 [Clase CMFCVisualManager](cmfcvisualmanager-class.md)
