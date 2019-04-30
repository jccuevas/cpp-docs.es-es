---
title: CAtlPreviewCtrlImpl Class
ms.date: 11/04/2016
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
helpviewer_keywords:
- CAtlPreviewCtrlImpl class
ms.assetid: 39b3299e-07e4-4abc-9b6e-b54bfa3b0802
ms.openlocfilehash: 71c50771889381ad2288637c23930103b5925a2c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246935"
---
# <a name="catlpreviewctrlimpl-class"></a>CAtlPreviewCtrlImpl Class

Esta clase es una implementación de ATL de una ventana que se coloca en una ventana host proporcionada por el Shell de vista previa avanzada.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::~CAtlPreviewCtrlImpl](#dtor)|Se destruye un objeto de control de vista previa.|
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|Construye un objeto de control de vista previa.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::Create](#create)|Llama a un controlador de vista previa avanzada para crear la ventana de Windows.|
|[CAtlPreviewCtrlImpl::Destroy](#destroy)|Se llama mediante un controlador de vista previa avanzada cuando es necesario destruir este control.|
|[CAtlPreviewCtrlImpl::Focus](#focus)|Establece el foco a este control de entrada.|
|[CAtlPreviewCtrlImpl::OnPaint](#onpaint)|Controla el mensaje WM_PAINT.|
|[CAtlPreviewCtrlImpl::Redraw](#redraw)|Indica que este control para volver a dibujar.|
|[CAtlPreviewCtrlImpl::SetHost](#sethost)|Establece a un nuevo elemento primario de este control.|
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Lo llama un controlador de vista previa avanzada cuando es necesario establecer los objetos visuales de vista previa enriquecida contenido.|
|[CAtlPreviewCtrlImpl::SetRect](#setrect)|Establece un nuevo rectángulo delimitador para este control.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::DoPaint](#dopaint)|Lo llama el marco de trabajo para representar la vista previa.|

### <a name="protected-constants"></a>Constantes protegidas

|Name|Descripción|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::m_plf](#m_plf)|Fuente utilizada para mostrar texto en la ventana Vista previa.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Name|Descripción|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::m_clrBack](#m_clrback)|Color de fondo de la ventana Vista previa.|
|[CAtlPreviewCtrlImpl::m_clrText](#m_clrtext)|Color del texto de la ventana de vista previa.|

## <a name="remarks"></a>Comentarios

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`TBase`

`ATL::CMessageMap`

`ATL::CWindowImplRoot<TBase>`

`ATL::CWindowImplBaseT<TBase,TWinTraits>`

[ATL::CWindowImpl\<CAtlPreviewCtrlImpl>](../../atl/reference/cwindowimpl-class.md)

`IPreviewCtrl`

`ATL::CAtlPreviewCtrlImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlpreviewctrlimpl.h

##  <a name="catlpreviewctrlimpl"></a>  CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl

Construye un objeto de control de vista previa.

```
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```

### <a name="remarks"></a>Comentarios

##  <a name="dtor"></a>  CAtlPreviewCtrlImpl::~CAtlPreviewCtrlImpl

Se destruye un objeto de control de vista previa.

```
virtual ~CAtlPreviewCtrlImpl(void);
```

### <a name="remarks"></a>Comentarios

##  <a name="create"></a>  CAtlPreviewCtrlImpl::Create

Llama a un controlador de vista previa avanzada para crear la ventana de Windows.

```
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```

### <a name="parameters"></a>Parámetros

*hWndParent*<br/>
Identificador de la ventana host proporcionada por el Shell de vista previa avanzada.

*prc*<br/>
Especifica el tamaño inicial y la posición de la ventana.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="destroy"></a>  CAtlPreviewCtrlImpl::Destroy

Se llama mediante un controlador de vista previa avanzada cuando es necesario destruir este control.

```
virtual void Destroy();
```

### <a name="remarks"></a>Comentarios

##  <a name="dopaint"></a>  CAtlPreviewCtrlImpl::DoPaint

Lo llama el marco de trabajo para representar la vista previa.

```
virtual void DoPaint(HDC hdc);
```

### <a name="parameters"></a>Parámetros

*hdc*<br/>
Identificador de un contexto de dispositivo para dibujar.

### <a name="remarks"></a>Comentarios

##  <a name="focus"></a>  CAtlPreviewCtrlImpl::Focus

Establece el foco a este control de entrada.

```
virtual void Focus();
```

### <a name="remarks"></a>Comentarios

##  <a name="m_clrback"></a>  CAtlPreviewCtrlImpl::m_clrBack

Color de fondo de la ventana Vista previa.

```
COLORREF m_clrBack;
```

### <a name="remarks"></a>Comentarios

##  <a name="m_clrtext"></a>  CAtlPreviewCtrlImpl::m_clrText

Color del texto de la ventana Vista previa.

```
COLORREF m_clrText;
```

### <a name="remarks"></a>Comentarios

##  <a name="m_plf"></a>  CAtlPreviewCtrlImpl::m_plf

Fuente utilizada para mostrar texto en la ventana Vista previa.

```
const LOGFONTW* m_plf;
```

### <a name="remarks"></a>Comentarios

##  <a name="onpaint"></a>  CAtlPreviewCtrlImpl::OnPaint

Controla el mensaje WM_PAINT.

```
LRESULT OnPaint(
    UINT nMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parámetros

*nMsg*<br/>
Se establece en WM_PAINT.

*wParam*<br/>
Este parámetro no se utiliza.

*lParam*<br/>
Este parámetro no se utiliza.

*bHandled*<br/>
Cuando esta función devuelve, contiene TRUE.

### <a name="return-value"></a>Valor devuelto

Siempre devuelve 0.

### <a name="remarks"></a>Comentarios

##  <a name="redraw"></a>  CAtlPreviewCtrlImpl::Redraw

Indica que este control para volver a dibujar.

```
virtual void Redraw();
```

### <a name="remarks"></a>Comentarios

##  <a name="sethost"></a>  CAtlPreviewCtrlImpl::SetHost

Establece a un nuevo elemento primario de este control.

```
virtual void SetHost(HWND hWndParent);
```

### <a name="parameters"></a>Parámetros

*hWndParent*<br/>
Identificador de la nueva ventana primaria.

### <a name="remarks"></a>Comentarios

##  <a name="setpreviewvisuals"></a>  CAtlPreviewCtrlImpl::SetPreviewVisuals

Lo llama un controlador de vista previa avanzada cuando es necesario establecer los objetos visuales de vista previa enriquecida contenido.

```
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```

### <a name="parameters"></a>Parámetros

*clrBack*<br/>
Color de fondo de la ventana Vista previa.

*clrText*<br/>
Color del texto de la ventana Vista previa.

*plf*<br/>
Fuente utilizada para mostrar texto en la ventana Vista previa.

### <a name="remarks"></a>Comentarios

##  <a name="setrect"></a>  CAtlPreviewCtrlImpl::SetRect

Establece un nuevo rectángulo delimitador para este control.

```
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```

### <a name="parameters"></a>Parámetros

*prc*<br/>
Especifica el nuevo tamaño y posición del control de vista previa.

*bRedraw*<br/>
Especifica si se debe dibujar el control.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md)
