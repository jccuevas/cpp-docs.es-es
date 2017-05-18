---
title: Clase CAtlPreviewCtrlImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Create
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Destroy
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Focus
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::OnPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Redraw
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetHost
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetPreviewVisuals
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetRect
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::DoPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_plf
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrBack
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrText
dev_langs:
- C++
helpviewer_keywords:
- CAtlPreviewCtrlImpl class
ms.assetid: 39b3299e-07e4-4abc-9b6e-b54bfa3b0802
caps.latest.revision: 26
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 979dc23eabc2ba2362f7301fc34ca89016d58f37
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="catlpreviewctrlimpl-class"></a>Clase CAtlPreviewCtrlImpl
Esta clase es una implementación de ATL de una ventana que se coloca en una ventana host proporcionada por el Shell para vista previa avanzada.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl:: ~ CAtlPreviewCtrlImpl](#dtor)|Destruye un objeto de control de vista previa.|  
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|Construye un objeto de control de vista previa.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::Create](#create)|Llama a un controlador de vista previa enriquecida para crear la ventana de Windows.|  
|[CAtlPreviewCtrlImpl::Destroy](#destroy)|Llama a un controlador de vista previa avanzada cuando es necesario destruir este control.|  
|[CAtlPreviewCtrlImpl::Focus](#focus)|Establece el foco a este control de entrada.|  
|[CAtlPreviewCtrlImpl::OnPaint](#onpaint)|Controla el mensaje WM_PAINT.|  
|[CAtlPreviewCtrlImpl::Redraw](#redraw)|Indica que este control vuelva a dibujar.|  
|[CAtlPreviewCtrlImpl::SetHost](#sethost)|Establece a un nuevo elemento primario para este control.|  
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Llama a un controlador de vista previa avanzada cuando es necesario establecer los elementos visuales de vista previa enriquecida contenido.|  
|[CAtlPreviewCtrlImpl::SetRect](#setrect)|Establece un nuevo rectángulo delimitador para este control.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::DoPaint](#dopaint)|Llamado por el marco para representar la vista previa.|  
  
### <a name="protected-constants"></a>Constantes protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::m_plf](#m_plf)|Fuente utilizada para mostrar texto en la ventana de vista previa.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::m_clrBack](#m_clrback)|Color de fondo de la ventana de vista previa.|  
|[CAtlPreviewCtrlImpl::m_clrText](#m_clrtext)|Color del texto de la ventana de vista previa.|  

  
## <a name="remarks"></a>Comentarios  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `TBase`  
  
 `ATL::CMessageMap`  
  
 `ATL::CWindowImplRoot<TBase>`  
  
 `ATL::CWindowImplBaseT<TBase,TWinTraits>`  
  
 [ATL::CWindowImpl\<CAtlPreviewCtrlImpl >](../../atl/reference/cwindowimpl-class.md)  
  
 `IPreviewCtrl`  
  
 `ATL::CAtlPreviewCtrlImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlpreviewctrlimpl.h  
  
##  <a name="catlpreviewctrlimpl"></a>CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl  
 Construye un objeto de control de vista previa.  
  
```
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="dtor"></a>CAtlPreviewCtrlImpl:: ~ CAtlPreviewCtrlImpl  
 Destruye un objeto de control de vista previa.  
  
```
virtual ~CAtlPreviewCtrlImpl(void);
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="create"></a>CAtlPreviewCtrlImpl::Create  
 Llama a un controlador de vista previa enriquecida para crear la ventana de Windows.  
  
```
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```  
  
### <a name="parameters"></a>Parámetros  
 `hWndParent`  
 Identificador de la ventana host proporcionada por el Shell para vista previa avanzada.  
  
 `prc`  
 Especifica el tamaño inicial y la posición de la ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si es correcto; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="destroy"></a>CAtlPreviewCtrlImpl::Destroy  
 Llama a un controlador de vista previa avanzada cuando es necesario destruir este control.  
  
```
virtual void Destroy();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="dopaint"></a>CAtlPreviewCtrlImpl::DoPaint  
 Llamado por el marco para representar la vista previa.  
  
```
virtual void DoPaint(HDC hdc);
```  
  
### <a name="parameters"></a>Parámetros  
 `hdc`  
 Identificador de un contexto de dispositivo para dibujar.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="focus"></a>CAtlPreviewCtrlImpl::Focus  
 Establece el foco a este control de entrada.  
  
```
virtual void Focus();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_clrback"></a>CAtlPreviewCtrlImpl::m_clrBack  
 Color de fondo de la ventana de vista previa.  
  
```
COLORREF m_clrBack;
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_clrtext"></a>CAtlPreviewCtrlImpl::m_clrText  
 Color del texto de la ventana de vista previa.  
  
```
COLORREF m_clrText;
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_plf"></a>CAtlPreviewCtrlImpl::m_plf  
 Fuente utilizada para mostrar texto en la ventana de vista previa.  
  
```
const LOGFONTW* m_plf;
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onpaint"></a>CAtlPreviewCtrlImpl::OnPaint  
 Controla el mensaje WM_PAINT.  
  
```
LRESULT OnPaint(  
    UINT nMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>Parámetros  
 `nMsg`  
 Establezca en WM_PAINT.  
  
 `wParam`  
 Este parámetro no se utiliza.  
  
 `lParam`  
 Este parámetro no se utiliza.  
  
 `bHandled`  
 Cuando esta función se devuelve, contiene `TRUE`.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="redraw"></a>CAtlPreviewCtrlImpl::Redraw  
 Indica que este control vuelva a dibujar.  
  
```
virtual void Redraw();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="sethost"></a>CAtlPreviewCtrlImpl::SetHost  
 Establece a un nuevo elemento primario para este control.  
  
```
virtual void SetHost(HWND hWndParent);
```  
  
### <a name="parameters"></a>Parámetros  
 `hWndParent`  
 Identificador de la nueva ventana primaria.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setpreviewvisuals"></a>CAtlPreviewCtrlImpl::SetPreviewVisuals  
 Llama a un controlador de vista previa avanzada cuando es necesario establecer los elementos visuales de vista previa enriquecida contenido.  
  
```
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```  
  
### <a name="parameters"></a>Parámetros  
 `clrBack`  
 Color de fondo de la ventana de vista previa.  
  
 `clrText`  
 Color del texto de la ventana de vista previa.  
  
 `plf`  
 Fuente utilizada para mostrar texto en la ventana de vista previa.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setrect"></a>CAtlPreviewCtrlImpl::SetRect  
 Establece un nuevo rectángulo delimitador para este control.  
  
```
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```  
  
### <a name="parameters"></a>Parámetros  
 `prc`  
 Especifica el nuevo tamaño y la posición del control de vista previa.  
  
 `bRedraw`  
 Especifica si debe volver a dibujar el control.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Componentes de escritorio de COM de ATL](../../atl/atl-com-desktop-components.md)

