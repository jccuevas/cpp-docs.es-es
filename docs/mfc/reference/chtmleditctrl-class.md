---
title: Clase CHtmlEditCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHtmlEditCtrl
dev_langs:
- C++
helpviewer_keywords:
- CHtmlEditCtrl class
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
caps.latest.revision: 22
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 4aca52508663e94ee9a1b55843ad05613aa40b0b
ms.lasthandoff: 02/24/2017

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
|[CHtmlEditCtrl::Create](#create)|Crea un control WebBrowser ActiveX y lo adjunta a la `CHtmlEditCtrl` objeto. Esta función coloca automáticamente el control WebBrowser ActiveX en modo de edición.|  
|[CHtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|Recupera el [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) interfaz en el documento cargado actualmente en el control WebBrowser independiente.|  
|[CHtmlEditCtrl::GetStartDocument](#getstartdocument)|Recupera la dirección URL a un documento predeterminado para cargar en el control WebBrowser independiente.|  
  
## <a name="remarks"></a>Comentarios  
 El control WebBrowser hospedado control se coloca automáticamente en el modo de edición después de crearlo.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHtmlEditCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxhtml.h  
  
##  <a name="a-namechtmleditctrla--chtmleditctrlchtmleditctrl"></a><a name="chtmleditctrl"></a>CHtmlEditCtrl::CHtmlEditCtrl  
 Construye un objeto `CHtmlEditCtrl`.  
  
```  
CHtmlEditCtrl();
```  
  
##  <a name="a-namecreatea--chtmleditctrlcreate"></a><a name="create"></a>CHtmlEditCtrl::Create  
 Crea un control WebBrowser ActiveX y lo adjunta a la `CHtmlEditCtrl` objeto. WebBrowser ActiveX control navega automáticamente a un documento predeterminado y, a continuación, se coloca en modo de edición por esta función.  
  
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
 Devuelve **TRUE** correctamente, **FALSE** en caso de error.  
  
##  <a name="a-namegetdhtmldocumenta--chtmleditctrlgetdhtmldocument"></a><a name="getdhtmldocument"></a>CHtmlEditCtrl::GetDHtmlDocument  
 Recupera el [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) interfaz en el documento cargado actualmente en el control WebBrowser independiente  
  
```  
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `ppDocument`  
 La interfaz de documento.  
  
##  <a name="a-namegetstartdocumenta--chtmleditctrlgetstartdocument"></a><a name="getstartdocument"></a>CHtmlEditCtrl::GetStartDocument  
 Recupera la dirección URL a un documento predeterminado para cargar en el control WebBrowser independiente.  
  
```  
virtual LPCTSTR GetStartDocument();
```  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)


