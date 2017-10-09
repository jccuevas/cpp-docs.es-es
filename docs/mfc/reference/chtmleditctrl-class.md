---
title: Clase CHtmlEditCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: 8a4cdfd1f11a3420f2d7ec46b1a30bb3eaf20a30
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="chtmleditctrl-class"></a>Clase CHtmlEditCtrl
Proporciona la funcionalidad del control ActiveX de WebBrowser en una ventana de MFC.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CHtmlEditCtrl: public CWnd,   
    public CHtmlEditCtrlBase<CHtmlEditCtrl>  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CHtmlEditCtrl::CHtmlEditCtrl](#chtmleditctrl)|Construye un objeto `CHtmlEditCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CHtmlEditCtrl::Create](#create)|Crea un control WebBrowser ActiveX y lo adjunta a la `CHtmlEditCtrl` objeto. Esta función coloca automáticamente el control ActiveX de WebBrowser en modo de edición.|  
|[CHtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|Recupera el [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) interfaz en el documento cargado actualmente en el control WebBrowser independiente.|  
|[CHtmlEditCtrl::GetStartDocument](#getstartdocument)|Recupera la dirección URL a un documento predeterminado para cargar en el control WebBrowser independiente.|  
  
## <a name="remarks"></a>Comentarios  
 El control WebBrowser hospedado control se pone automáticamente en modo de edición después de crearlo.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHtmlEditCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxhtml.h  
  
##  <a name="chtmleditctrl"></a>CHtmlEditCtrl::CHtmlEditCtrl  
 Construye un objeto `CHtmlEditCtrl`.  
  
```  
CHtmlEditCtrl();
```  
  
##  <a name="create"></a>CHtmlEditCtrl::Create  
 Crea un control WebBrowser ActiveX y lo adjunta a la `CHtmlEditCtrl` objeto. El WebBrowser ActiveX control navega automáticamente a un documento predeterminado y, a continuación, se coloca en modo de edición por esta función.  
  
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
 `lpszWindowName`  
 Este parámetro no se utiliza.  
  
 `dwStyle`  
 Este parámetro no se utiliza.  
  
 `rect`  
 Especifica el tamaño y la posición del control.  
  
 `pParentWnd`  
 Especifica la ventana del control primario. No debe ser **NULL**.  
  
 `nID`  
 Especifica el identificador. del control  
  
 `pContext`  
 Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
##  <a name="getdhtmldocument"></a>CHtmlEditCtrl::GetDHtmlDocument  
 Recupera el [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) interfaz en el documento cargado actualmente en el control WebBrowser independiente  
  
```  
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `ppDocument`  
 La interfaz de documentos.  
  
##  <a name="getstartdocument"></a>CHtmlEditCtrl::GetStartDocument  
 Recupera la dirección URL a un documento predeterminado para cargar en el control WebBrowser independiente.  
  
```  
virtual LPCTSTR GetStartDocument();
```  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)


