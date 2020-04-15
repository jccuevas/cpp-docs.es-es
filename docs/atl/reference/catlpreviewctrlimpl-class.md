---
title: Clase CAtlPreviewCtrlImpl
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
ms.openlocfilehash: 1ccd01bc4d48dc088538f4799b595cce3fb910ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321367"
---
# <a name="catlpreviewctrlimpl-class"></a>Clase CAtlPreviewCtrlImpl

Esta clase es una implementación ATL de una ventana que se coloca en una ventana host proporcionada por el Shell para vista previa enriquecida.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::-CAtlPreviewCtrlImpl](#dtor)|Destruye un objeto de control de vista previa.|
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|Construye un objeto de control de vista previa.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::Crear](#create)|Llamado por un controlador de vista previa enriquecida para crear la ventana de Windows.|
|[CAtlPreviewCtrlImpl::Destroy](#destroy)|Llamado por un controlador de vista previa enriquecida cuando necesita destruir este control.|
|[CAtlPreviewCtrlImpl::Focus](#focus)|Establece el foco de entrada en este control.|
|[CAtlPreviewCtrlImpl::OnPaint](#onpaint)|Controla el mensaje de WM_PAINT.|
|[CAtlPreviewCtrlImpl::Redraw](#redraw)|Le dice a este control que vuelva a dibujar.|
|[CAtlPreviewCtrlImpl::SetHost](#sethost)|Establece un nuevo elemento primario para este control.|
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Llamado por un controlador de vista previa enriquecida cuando necesita establecer objetos visuales de contenido de vista previa enriquecido.|
|[CAtlPreviewCtrlImpl::SetRect](#setrect)|Establece un nuevo rectángulo delimitador para este control.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::DoPaint](#dopaint)|Llamado por el marco de trabajo para representar la vista previa.|

### <a name="protected-constants"></a>Constantes protegidas

|Nombre|Descripción|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::m_plf](#m_plf)|Fuente utilizada para mostrar texto en la ventana de vista previa.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::m_clrBack](#m_clrback)|Color de fondo de la ventana de vista previa.|
|[CAtlPreviewCtrlImpl::m_clrText](#m_clrtext)|Color del texto de la ventana de vista previa.|

## <a name="remarks"></a>Observaciones

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

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="catlpreviewctrlimpl"></a>CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl

Construye un objeto de control de vista previa.

```
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```

### <a name="remarks"></a>Observaciones

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="dtor"></a>CAtlPreviewCtrlImpl::-CAtlPreviewCtrlImpl

Destruye un objeto de control de vista previa.

```
virtual ~CAtlPreviewCtrlImpl(void);
```

### <a name="remarks"></a>Observaciones

## <a name="catlpreviewctrlimplcreate"></a><a name="create"></a>CAtlPreviewCtrlImpl::Crear

Llamado por un controlador de vista previa enriquecida para crear la ventana de Windows.

```
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```

### <a name="parameters"></a>Parámetros

*hWndParent*<br/>
Identificador de la ventana host proporcionada por el Shell para vista previa enriquecida.

*Prc*<br/>
Especifica el tamaño inicial y la posición de la ventana.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

## <a name="catlpreviewctrlimpldestroy"></a><a name="destroy"></a>CAtlPreviewCtrlImpl::Destroy

Llamado por un controlador de vista previa enriquecida cuando necesita destruir este control.

```
virtual void Destroy();
```

### <a name="remarks"></a>Observaciones

## <a name="catlpreviewctrlimpldopaint"></a><a name="dopaint"></a>CAtlPreviewCtrlImpl::DoPaint

Llamado por el marco de trabajo para representar la vista previa.

```
virtual void DoPaint(HDC hdc);
```

### <a name="parameters"></a>Parámetros

*Hdc*<br/>
Identificador de un contexto de dispositivo para pintar.

### <a name="remarks"></a>Observaciones

## <a name="catlpreviewctrlimplfocus"></a><a name="focus"></a>CAtlPreviewCtrlImpl::Focus

Establece el foco de entrada en este control.

```
virtual void Focus();
```

### <a name="remarks"></a>Observaciones

## <a name="catlpreviewctrlimplm_clrback"></a><a name="m_clrback"></a>CAtlPreviewCtrlImpl::m_clrBack

Color de fondo de la ventana de vista previa.

```
COLORREF m_clrBack;
```

### <a name="remarks"></a>Observaciones

## <a name="catlpreviewctrlimplm_clrtext"></a><a name="m_clrtext"></a>CAtlPreviewCtrlImpl::m_clrText

Color de texto de la ventana de vista previa.

```
COLORREF m_clrText;
```

### <a name="remarks"></a>Observaciones

## <a name="catlpreviewctrlimplm_plf"></a><a name="m_plf"></a>CAtlPreviewCtrlImpl::m_plf

Fuente utilizada para mostrar texto en la ventana de vista previa.

```
const LOGFONTW* m_plf;
```

### <a name="remarks"></a>Observaciones

## <a name="catlpreviewctrlimplonpaint"></a><a name="onpaint"></a>CAtlPreviewCtrlImpl::OnPaint

Controla el mensaje de WM_PAINT.

```
LRESULT OnPaint(
    UINT nMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parámetros

*nMsg*<br/>
Establézalo en WM_PAINT.

*wParam*<br/>
Este parámetro no se utiliza.

*lParam*<br/>
Este parámetro no se utiliza.

*bHandled*<br/>
Cuando se devuelve esta función, contiene TRUE.

### <a name="return-value"></a>Valor devuelto

Siempre devuelve 0.

### <a name="remarks"></a>Observaciones

## <a name="catlpreviewctrlimplredraw"></a><a name="redraw"></a>CAtlPreviewCtrlImpl::Redraw

Le dice a este control que vuelva a dibujar.

```
virtual void Redraw();
```

### <a name="remarks"></a>Observaciones

## <a name="catlpreviewctrlimplsethost"></a><a name="sethost"></a>CAtlPreviewCtrlImpl::SetHost

Establece un nuevo elemento primario para este control.

```
virtual void SetHost(HWND hWndParent);
```

### <a name="parameters"></a>Parámetros

*hWndParent*<br/>
Identificador de la nueva ventana primaria.

### <a name="remarks"></a>Observaciones

## <a name="catlpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>CAtlPreviewCtrlImpl::SetPreviewVisuals

Llamado por un controlador de vista previa enriquecida cuando necesita establecer objetos visuales de contenido de vista previa enriquecido.

```
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```

### <a name="parameters"></a>Parámetros

*clrBack*<br/>
Color de fondo de la ventana de vista previa.

*clrText*<br/>
Color de texto de la ventana de vista previa.

*Plf*<br/>
Fuente utilizada para mostrar texto en la ventana de vista previa.

### <a name="remarks"></a>Observaciones

## <a name="catlpreviewctrlimplsetrect"></a><a name="setrect"></a>CAtlPreviewCtrlImpl::SetRect

Establece un nuevo rectángulo delimitador para este control.

```
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```

### <a name="parameters"></a>Parámetros

*Prc*<br/>
Especifica el nuevo tamaño y la posición del control de vista previa.

*bRedraw*<br/>
Especifica si se debe volver a dibujar el control.

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md)
