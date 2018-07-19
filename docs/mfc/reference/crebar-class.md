---
title: CReBar (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CReBar
- AFXEXT/CReBar
- AFXEXT/CReBar::AddBar
- AFXEXT/CReBar::Create
- AFXEXT/CReBar::GetReBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- CReBar [MFC], AddBar
- CReBar [MFC], Create
- CReBar [MFC], GetReBarCtrl
ms.assetid: c1ad2720-1d33-4106-8e4e-80aa84f93559
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1acc2d5918bea040e1f004e8a1d11ceee3146f89
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848624"
---
# <a name="crebar-class"></a>CReBar (clase)
Barra de control que proporciona información de diseño, persistencia y estado para controles rebar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CReBar : public CControlBar  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CReBar::AddBar](#addbar)|Agrega una banda a un control rebar.|  
|[CReBar::Create](#create)|Crea el control rebar y lo adjunta a la `CReBar` objeto.|  
|[CReBar:: GetReBarCtrl](#getrebarctrl)|Permite el acceso directo al control subyacente común.|  
  
## <a name="remarks"></a>Comentarios  
 Un objeto rebar puede contener una variedad de las ventanas secundarias, normalmente otros controles, incluidos los cuadros de edición, barras de herramientas y cuadros de lista. Un objeto rebar puede mostrar sus ventanas secundarias a través de un mapa de bits especificado. La aplicación puede cambiar el tamaño del rebar automáticamente, o el usuario puede cambiar manualmente el tamaño del rebar haciendo clic o arrastrando su barra de controles.  
  
 ![Ejemplo de RebarMenu](../../mfc/reference/media/vc4sc61.gif "vc4sc61")  
  
## <a name="rebar-control"></a>Control rebar  
 Un objeto rebar se comporta de forma similar a un objeto de barra de herramientas. Un control rebar utiliza el mecanismo de hacer clic y arrastrar para cambiar el tamaño de sus bandas. Un control rebar puede contener una o más bandas con cada banda puede tener cualquier combinación de una barra de controles, un mapa de bits, una etiqueta de texto y una ventana secundaria. Sin embargo, las bandas no pueden contener más de una ventana secundaria.  
  
 `CReBar` usa el [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) clase para proporcionar su implementación. Puede tener acceso el control rebar a través de [GetReBarCtrl](#getrebarctrl) para aprovechar las ventajas de las opciones de personalización del control. Para obtener más información acerca de los controles rebar, consulte `CReBarCtrl`. Para obtener más información sobre el uso de los controles rebar, consulte [usar CReBarCtrl](../../mfc/using-crebarctrl.md).  
  
> [!CAUTION]
>  Rebar y objetos de control rebar no admiten el control MFC de la barra de acoplamiento. Si `CRebar::EnableDocking` se llama, la aplicación se producirá una aserción.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CReBar`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxext.h  
  
##  <a name="addbar"></a>  CReBar::AddBar  
 Llame a esta función miembro para agregar una banda en el control rebar.  
  
```  
BOOL AddBar(
    CWnd* pBar,  
    LPCTSTR pszText = NULL,  
    CBitmap* pbmp = NULL,  
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

 
BOOL AddBar(
    CWnd* pBar,  
    COLORREF clrFore,  
    COLORREF clrBack,  
    LPCTSTR pszText = NULL,  
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```  
  
### <a name="parameters"></a>Parámetros  
 *pBar*  
 Un puntero a un `CWnd` objeto que es la ventana secundaria va a insertar en el control rebar. El objeto que se hace referencia debe tener un WS_CHILD.  
  
 *lpszText*  
 Un puntero a una cadena que contiene el texto que aparece en el control rebar. NULL de forma predeterminada. El texto contenido en *lpszText* no forma parte de la ventana secundaria; se encuentra en el propio control de rebar.  
  
 *pbmp*  
 Un puntero a un `CBitmap` objeto se muestre en el fondo del control rebar. NULL de forma predeterminada.  
  
 *dwStyle*  
 DWORD que contiene el estilo que se aplicará para el control rebar. Consulte la `fStyle` descripción de la estructura de Win32 de la función [REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) para obtener una lista completa de los estilos de banda.  
  
 *clrFore*  
 Un valor COLORREF que representa el color de primer plano del control rebar.  
  
 *clrBack*  
 Un valor COLORREF que representa el color de fondo del control rebar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]  
  
##  <a name="create"></a>  CReBar::Create  
 Llame a esta función miembro para crear un control rebar.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = RBS_BANDBORDERS,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,  
    UINT nID = AFX_IDW_REBAR);
```  
  
### <a name="parameters"></a>Parámetros  
 *pParentWnd*  
 Puntero a la `CWnd` objeto cuya ventana de Windows es el elemento primario de la barra de estado. Normalmente, la ventana de marco.  
  
 *dwCtrlStyle*  
 El estilo del control rebar. De forma predeterminada, RBS_BANDBORDERS, que muestra la estrechas líneas para separar las bandas adyacentes dentro del control rebar. Consulte [estilos del Control Rebar](http://msdn.microsoft.com/library/windows/desktop/bb774377) en el SDK de Windows para obtener una lista de estilos.  
  
 *dwStyle*  
 Los estilos de ventana rebar.  
  
 *nID*  
 Identificador de ventana secundaria. del control rebar  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CReBar::AddBar](#addbar).  
  
##  <a name="getrebarctrl"></a>  CReBar:: GetReBarCtrl  
 Esta función miembro permite el acceso directo al control subyacente común.  
  
```  
CReBarCtrl& GetReBarCtrl() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a un [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para aprovechar la funcionalidad del control común de rebar Windows en la personalización de su control rebar. Cuando se llama a `GetReBarCtrl`, devuelve un objeto de referencia para el `CReBarCtrl` por lo que puede usar cualquier conjunto de funciones miembro de objeto.  
  
 Para obtener más información sobre el uso de `CReBarCtrl` para personalizar su rebar, consulte [usar CReBarCtrl](../../mfc/using-crebarctrl.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFCIE de MFC](../../visual-cpp-samples.md)   
 [CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



