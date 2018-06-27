---
title: Clase CCommonDialog | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCommonDialog
- AFXDLGS/CCommonDialog
- AFXDLGS/CCommonDialog::CCommonDialog
dev_langs:
- C++
helpviewer_keywords:
- CCommonDialog [MFC], CCommonDialog
ms.assetid: 1f68d65f-a0fd-4778-be22-ebbe51a95f95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 53f53bdb19c6f40d73179b600051ecfaf6b69c94
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950640"
---
# <a name="ccommondialog-class"></a>Clase CCommonDialog
La clase base para las clases que encapsulan la funcionalidad de los cuadros de diálogo comunes de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CCommonDialog : public CDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCommonDialog::CCommonDialog](#ccommondialog)|Construye un objeto `CCommonDialog`.|  
  
## <a name="remarks"></a>Comentarios  
 Las clases siguientes encapsulan la funcionalidad de los cuadros de diálogo comunes de Windows:  
  
- [CFileDialog](../../mfc/reference/cfiledialog-class.md)  
  
- [CFontDialog](../../mfc/reference/cfontdialog-class.md)  
  
- [CColorDialog](../../mfc/reference/ccolordialog-class.md)  
  
- [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)  
  
- [CPrintDialog](../../mfc/reference/cprintdialog-class.md)  
  
- [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)  
  
- [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)  
  
- [COleDialog](../../mfc/reference/coledialog-class.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `CCommonDialog`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdlgs.h  
  
##  <a name="ccommondialog"></a>  CCommonDialog::CCommonDialog  
 Construye un objeto `CCommonDialog`.  
  
```  
explicit CCommonDialog(CWnd* pParentWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 *pParentWnd*  
 Señala al objeto de ventana primaria o propietaria (de tipo [CWnd](../../mfc/reference/cwnd-class.md)) a la que pertenece el objeto de cuadro de diálogo. Si es **NULL**, ventana primaria del objeto de cuadro de diálogo se establece en la ventana de la aplicación principal.  
  
### <a name="remarks"></a>Comentarios  
 Vea [CDialog::CDialog](../../mfc/reference/cdialog-class.md#cdialog) para obtener información completa.  
  
## <a name="see-also"></a>Vea también  
 [CDialog (clase)](../../mfc/reference/cdialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFileDialog (clase)](../../mfc/reference/cfiledialog-class.md)   
 [Clase CFontDialog](../../mfc/reference/cfontdialog-class.md)   
 [Clase CColorDialog](../../mfc/reference/ccolordialog-class.md)   
 [Clase CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)   
 [Clase CPrintDialog](../../mfc/reference/cprintdialog-class.md)   
 [Clase CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)   
 [COleDialog (clase)](../../mfc/reference/coledialog-class.md)
