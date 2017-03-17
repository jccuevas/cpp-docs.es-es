---
title: CReBar (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- rebar controls, control bar
- CReBar class
- Internet Explorer 4.0 common controls
ms.assetid: c1ad2720-1d33-4106-8e4e-80aa84f93559
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
ms.openlocfilehash: 38ac4611503bec70ea9f809a4d4f9d4b5133e30e
ms.lasthandoff: 02/24/2017

---
# <a name="crebar-class"></a>CReBar (clase)
Barra de control que proporciona información de diseño, persistencia y estado para controles rebar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CReBar : public CControlBar  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CReBar::AddBar](#addbar)|Agrega una banda a un control rebar.|  
|[CReBar::Create](#create)|Crea el control rebar y lo adjunta a la `CReBar` objeto.|  
|[CReBar:: GetReBarCtrl](#getrebarctrl)|Permite el acceso directo al control subyacente común.|  
  
## <a name="remarks"></a>Comentarios  
 Un objeto rebar puede contener una variedad de ventanas secundarias, normalmente otros controles, incluidos los cuadros de edición, barras de herramientas y cuadros de lista. Un objeto rebar puede mostrar sus ventanas secundarias sobre un mapa de bits especificado. La aplicación puede cambiar de tamaño automáticamente el control rebar o el usuario puede cambiar el tamaño manualmente el control rebar haciendo clic o arrastrando su barra de controles.  
  
 ![Ejemplo de RebarMenu](../../mfc/reference/media/vc4sc61.gif "vc4sc61")  
  
## <a name="rebar-control"></a>Control rebar  
 Un objeto rebar se comporta de forma similar a un objeto de barra de herramientas. Un control rebar utiliza el mecanismo de clic y arrastrar para cambiar el tamaño de sus bandas. Un control rebar puede contener una o más bandas, con cada banda puede tener cualquier combinación de una barra de controles, un mapa de bits, una etiqueta de texto y una ventana secundaria. Sin embargo, las bandas no pueden contener más de una ventana secundaria.  
  
 **CReBar** utiliza la [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) clase para proporcionar su implementación. Puede tener acceso el control rebar a través de [GetReBarCtrl](#getrebarctrl) aprovechar las opciones de personalización del control. Para obtener más información acerca de los controles rebar, consulte `CReBarCtrl`. Para obtener más información acerca del uso de controles rebar, consulte [CReBarCtrl utilizando](../../mfc/using-crebarctrl.md).  
  
> [!CAUTION]
>  Rebar y objetos de control rebar no admiten el control MFC de la barra de acoplamiento. Si **CRebar::EnableDocking** se llama, la aplicación producirá una aserción.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CReBar`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxext.h  
  
##  <a name="addbar"></a>CReBar::AddBar  
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
 `pBar`  
 Un puntero a un `CWnd` objeto de la ventana secundaria que va a insertar en el control rebar. El objeto de referencia debe tener un **WS_CHILD**.  
  
 `lpszText`  
 Puntero a una cadena que contiene el texto que aparece en el control rebar. **NULL** de forma predeterminada. El texto incluido en `lpszText` no es parte de la ventana secundaria; está en el control rebar propio.  
  
 `pbmp`  
 Un puntero a un `CBitmap` objeto se muestre en el fondo del control rebar. **NULL** de forma predeterminada.  
  
 `dwStyle`  
 Un `DWORD` que contiene el estilo que se va a aplicar al control rebar. Consulte la **fStyle** descripción de la estructura de Win32 de la función [REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) para obtener una lista completa de los estilos de banda.  
  
 *clrFore*  
 Un **COLORREF** valor que representa el color de primer plano del control rebar.  
  
 *clrBack*  
 Un **COLORREF** valor que representa el color de fondo del control rebar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[1 NVC_MFC_CReBarCtrl](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]  
  
##  <a name="create"></a>CReBar::Create  
 Llame a esta función miembro para crear un control rebar.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = RBS_BANDBORDERS,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,  
    UINT nID = AFX_IDW_REBAR);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentWnd`  
 Puntero a la `CWnd` objeto cuya ventana de Windows es el elemento primario de la barra de estado. Normalmente, la ventana de marco.  
  
 `dwCtrlStyle`  
 El estilo del control rebar. De forma predeterminada, **RBS_BANDBORDERS**, que muestra restringir líneas para separar las bandas adyacentes dentro del control rebar. Consulte [estilos de Control Rebar](http://msdn.microsoft.com/library/windows/desktop/bb774377) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una lista de estilos.  
  
 `dwStyle`  
 Los estilos de ventana rebar.  
  
 `nID`  
 Identificador de ventana secundaria. de rebar  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CReBar::AddBar](#addbar).  
  
##  <a name="getrebarctrl"></a>CReBar:: GetReBarCtrl  
 Esta función miembro permite el acceso directo al control subyacente común.  
  
```  
CReBarCtrl& GetReBarCtrl() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a un [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para aprovechar la funcionalidad del control común rebar Windows para personalizar su rebar. Cuando se llama a `GetReBarCtrl`, devuelve un objeto de referencia para la `CReBarCtrl` para que pueda usar cualquier conjunto de funciones miembro de objeto.  
  
 Para obtener más información acerca del uso de `CReBarCtrl` para personalizar su rebar, consulte [CReBarCtrl utilizando](../../mfc/using-crebarctrl.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CReBarCtrl&#2;](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Este ejemplo de MFC](../../visual-cpp-samples.md)   
 [CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




