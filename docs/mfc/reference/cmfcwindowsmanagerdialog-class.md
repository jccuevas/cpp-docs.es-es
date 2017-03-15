---
title: Clase CMFCWindowsManagerDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCWindowsManagerDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCWindowsManagerDialog class
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
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
ms.openlocfilehash: 9f1508cfd3844fed413edd69063f1b3e64e80195
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcwindowsmanagerdialog-class"></a>Clase CMFCWindowsManagerDialog
La `CMFCWindowsManagerDialog` objeto permite al usuario administrar ventanas secundarias MDI en una aplicación MDI.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCWindowsManagerDialog : public CDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCWindowsManagerDialog::CMFCWindowsManagerDialog](#cmfcwindowsmanagerdialog)|Construye un objeto `CMFCWindowsManagerDialog`.|  
  
## <a name="remarks"></a>Comentarios  
 El `CMFCWindowsManagerDialog` contiene una lista de ventanas secundarias MDI que están abiertos actualmente en la aplicación. El usuario puede controlar manualmente el estado de las ventanas secundarias MDI mediante este cuadro de diálogo.  
  
 `CMFCWindowsManagerDialog`está incrustado en el [CMDIFrameWndEx Class](../../mfc/reference/cmdiframewndex-class.md). El `CMFCWindowsManagerDialog` no es una clase que debe crear manualmente. En su lugar, llame a la función [CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog), y crear y mostrar un `CMFCWindowsManagerDialog` objeto.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un `CMFCWindowsManagerDialog` objeto mediante una llamada a `CMDIFrameWndEx::ShowWindowsDialog`. Este fragmento de código forma parte de la [ejemplo de demostración de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#18;](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxWindowsManagerDialog.h  
  
##  <a name="a-namecmfcwindowsmanagerdialoga--cmfcwindowsmanagerdialogcmfcwindowsmanagerdialog"></a><a name="cmfcwindowsmanagerdialog"></a>CMFCWindowsManagerDialog::CMFCWindowsManagerDialog  
 Construye un [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) objeto.  
  
```  
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,  
    BOOL bHelpButton = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMDIFrame`  
 Puntero a la ventana primaria o propietaria.  
  
 [in] `bHelpButton`  
 Un parámetro booleano que especifica si el marco de trabajo muestra un **ayuda** botón.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de los administradores visuales, vea [Administrador de visualización](../../mfc/visualization-manager.md).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMDIFrameWndEx Class](../../mfc/reference/cmdiframewndex-class.md)

