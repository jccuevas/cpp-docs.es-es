---
title: CHtmlEditCtrl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::Create
- AFXHTML/CHtmlEditCtrl::GetDHtmlDocument
- AFXHTML/CHtmlEditCtrl::GetStartDocument
dev_langs:
- C++
helpviewer_keywords:
- CHtmlEditCtrl [MFC], CHtmlEditCtrl
- CHtmlEditCtrl [MFC], Create
- CHtmlEditCtrl [MFC], GetDHtmlDocument
- CHtmlEditCtrl [MFC], GetStartDocument
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4cc8cdc389edc8abbc424ec8277f759e7f3d81bb
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338573"
---
# <a name="chtmleditctrl-class"></a>CHtmlEditCtrl (clase)
Proporciona la funcionalidad del control ActiveX de WebBrowser en una ventana de MFC.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CHtmlEditCtrl: public CWnd,   
    public CHtmlEditCtrlBase<CHtmlEditCtrl>  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHtmlEditCtrl::CHtmlEditCtrl](#chtmleditctrl)|Construye un objeto `CHtmlEditCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHtmlEditCtrl::Create](#create)|Crea un control WebBrowser ActiveX y lo adjunta a la `CHtmlEditCtrl` objeto. Esta función coloca automáticamente el control WebBrowser ActiveX en modo de edición.|  
|[CHtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|Recupera el [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) interfaz en el documento cargado actualmente en el control WebBrowser independiente.|  
|[CHtmlEditCtrl::GetStartDocument](#getstartdocument)|Recupera la dirección URL a un documento predeterminado para cargar en el control WebBrowser independiente.|  
  
## <a name="remarks"></a>Comentarios  
 Hospedado WebBrowser control se pone automáticamente en modo de edición después de crearlo.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHtmlEditCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxhtml.h  
  
##  <a name="chtmleditctrl"></a>  CHtmlEditCtrl::CHtmlEditCtrl  
 Construye un objeto `CHtmlEditCtrl`.  
  
```  
CHtmlEditCtrl();
```  
  
##  <a name="create"></a>  CHtmlEditCtrl::Create  
 Crea un control WebBrowser ActiveX y lo adjunta a la `CHtmlEditCtrl` objeto. Modo de edición WebBrowser ActiveX control navega automáticamente a un documento predeterminado y, a continuación, se coloca en esta función.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    int nID,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszWindowName*  
 Este parámetro no se utiliza.  
  
 *dwStyle*  
 Este parámetro no se utiliza.  
  
 *Rect*  
 Especifica el tamaño y la posición del control.  
  
 *pParentWnd*  
 Especifica la ventana del control primario. No debe ser NULL.  
  
 *nID*  
 Especifica el identificador. del control  
  
 *pContext*  
 Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
##  <a name="getdhtmldocument"></a>  CHtmlEditCtrl::GetDHtmlDocument  
 Recupera el [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) interfaz en el documento cargado actualmente en el control WebBrowser independiente  
  
```  
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *ppDocument*  
 La interfaz de documento.  
  
##  <a name="getstartdocument"></a>  CHtmlEditCtrl::GetStartDocument  
 Recupera la dirección URL a un documento predeterminado para cargar en el control WebBrowser independiente.  
  
```  
virtual LPCTSTR GetStartDocument();
```  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)

