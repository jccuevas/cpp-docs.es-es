---
title: Clase CStockPropImpl
ms.date: 05/06/2019
f1_keywords:
- CStockPropImpl
- ATLCTL/ATL::CStockPropImpl
- ATLCTL/ATL::get_Appearance
- ATLCTL/ATL::get_AutoSize
- ATLCTL/ATL::get_BackColor
- ATLCTL/ATL::get_BackStyle
- ATLCTL/ATL::get_BorderColor
- ATLCTL/ATL::get_BorderStyle
- ATLCTL/ATL::get_BorderVisible
- ATLCTL/ATL::get_BorderWidth
- ATLCTL/ATL::get_Caption
- ATLCTL/ATL::get_DrawMode
- ATLCTL/ATL::get_DrawStyle
- ATLCTL/ATL::get_DrawWidth
- ATLCTL/ATL::get_Enabled
- ATLCTL/ATL::get_FillColor
- ATLCTL/ATL::get_FillStyle
- ATLCTL/ATL::get_Font
- ATLCTL/ATL::get_ForeColor
- ATLCTL/ATL::get_HWND
- ATLCTL/ATL::get_MouseIcon
- ATLCTL/ATL::get_MousePointer
- ATLCTL/ATL::get_Picture
- ATLCTL/ATL::get_ReadyState
- ATLCTL/ATL::get_TabStop
- ATLCTL/ATL::get_Text
- ATLCTL/ATL::getvalid
- ATLCTL/ATL::get_Window
- ATLCTL/ATL::put_Appearance
- ATLCTL/ATL::put_AutoSize
- ATLCTL/ATL::put_BackColor
- ATLCTL/ATL::put_BackStyle
- ATLCTL/ATL::put_BorderColor
- ATLCTL/ATL::put_BorderStyle
- ATLCTL/ATL::put_BorderVisible
- ATLCTL/ATL::put_BorderWidth
- ATLCTL/ATL::put_Caption
- ATLCTL/ATL::put_DrawMode
- ATLCTL/ATL::put_DrawStyle
- ATLCTL/ATL::put_DrawWidth
- ATLCTL/ATL::put_Enabled
- ATLCTL/ATL::put_FillColor
- ATLCTL/ATL::put_FillStyle
- ATLCTL/ATL::put_Font
- ATLCTL/ATL::put_ForeColor
- ATLCTL/ATL::put_HWND
- ATLCTL/ATL::put_MouseIcon
- ATLCTL/ATL::put_MousePointer
- ATLCTL/ATL::put_Picture
- ATLCTL/ATL::put_ReadyState
- ATLCTL/ATL::put_TabStop
- ATLCTL/ATL::put_Text
- ATLCTL/ATL::putvalid
- ATLCTL/ATL::put_Window
- ATLCTL/ATL::putref_Font
- ATLCTL/ATL::putref_MouseIcon
- ATLCTL/ATL::putref_Picture
helpviewer_keywords:
- CStockPropImpl class
- controls [ATL], stock properties
- stock properties, ATL controls
ms.assetid: 45f11d7d-6580-4a0e-872d-3bc8b836cfda
ms.openlocfilehash: 0aaeb1b6de0febfd5fc0d41cbcc7bad41c607af4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330672"
---
# <a name="cstockpropimpl-class"></a>Clase CStockPropImpl

Esta clase proporciona métodos para admitir valores de propiedad de stock.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <
    class T,
    class InterfaceName,
    const IID* piid = &_ATL_IIDOF(InterfaceName),
    const GUID* plibid = &CComModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0,
    class tihclass = CcomTypeInfoHolder>
class ATL_NO_VTABLE CStockPropImpl :
    public IDispatchImpl<InterfaceName, piid, plibid, wMajor, wMinor, tihclass>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase que implementa el `CStockPropImpl`control y deriva de .

*InterfaceName*<br/>
Una interfaz dual que expone las propiedades de stock.

*piid*<br/>
Un puntero al IID de `InterfaceName`.

*plibid*<br/>
Puntero al LIBID de la biblioteca de `InterfaceName`tipos que contiene la definición de .

*wMajor*<br/>
La versión principal de la biblioteca de tipos. El valor predeterminado es 1.

*wMinor*<br/>
La versión secundaria de la biblioteca de tipos. El valor predeterminado es 0.

*tihclass*<br/>
La clase utilizada para gestionar la información de tipo para *T*. El valor `CComTypeInfoHolder`predeterminado es .

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|[get_Appearance](#get_appearance)|Llame a este método para obtener el estilo de pintura utilizado por el control, por ejemplo, plano o 3D.|
|[get_AutoSize](#get_autosize)|Llame a este método para obtener el estado de la marca que indica si el control no puede ser de otro tamaño.|
|[get_BackColor](#get_backcolor)|Llame a este método para obtener el color de fondo del control.|
|[get_BackStyle](#get_backstyle)|Llame a este método para obtener el estilo de fondo del control, transparente u opaco.|
|[get_BorderColor](#get_bordercolor)|Llame a este método para obtener el color del borde del control.|
|[get_BorderStyle](#get_borderstyle)|Llame a este método para obtener el estilo de borde del control.|
|[get_BorderVisible](#get_bordervisible)|Llame a este método para obtener el estado de la marca que indica si el borde del control está visible o no.|
|[get_BorderWidth](#get_borderwidth)|Llame a este método para obtener el ancho (en píxeles) del borde del control.|
|[get_Caption](#get_caption)|Llame a este método para obtener el texto especificado en el título de un objeto.|
|[get_DrawMode](#get_drawmode)|Llame a este método para obtener el modo de dibujo del control, por ejemplo, XOR Pen o Invertir colores.|
|[get_DrawStyle](#get_drawstyle)|Llame a este método para obtener el estilo de dibujo del control, por ejemplo, sólido, discontinuo o punteado.|
|[get_DrawWidth](#get_drawwidth)|Llame a este método para obtener el ancho del dibujo (en píxeles) utilizado por los métodos de dibujo del control.|
|[get_Enabled](#get_enabled)|Llame a este método para obtener el estado de la marca que indica si el control está habilitado.|
|[get_FillColor](#get_fillcolor)|Llame a este método para obtener el color de relleno del control.|
|[get_FillStyle](#get_fillstyle)|Llame a este método para obtener el estilo de relleno del control, por ejemplo, sólido, transparente o rayado cruzado.|
|[get_Font](#get_font)|Llame a este método para obtener un puntero a las propiedades de fuente del control.|
|[get_ForeColor](#get_forecolor)|Llame a este método para obtener el color de primer plano del control.|
|[get_HWND](#get_hwnd)|Llame a este método para obtener el identificador de ventana asociado con el control.|
|[get_MouseIcon](#get_mouseicon)|Llame a este método para obtener las propiedades de imagen del gráfico (icono, mapa de bits o metarchivo) que se mostrará cuando el mouse está sobre el control.|
|[get_MousePointer](#get_mousepointer)|Llame a este método para obtener el tipo de puntero del mouse que se muestra cuando el mouse está sobre el control, por ejemplo, flecha, cruz o reloj de arena.|
|[get_Picture](#get_picture)|Llame a este método para obtener un puntero a las propiedades de imagen de un gráfico (icono, mapa de bits o metarchivo) que se va a mostrar.|
|[get_ReadyState](#get_readystate)|Llame a este método para obtener el estado listo del control, por ejemplo, cargar o cargar.|
|[get_TabStop](#get_tabstop)|Llame a este método para obtener la marca que indica si el control es una tabulación o no.|
|[get_Text](#get_text)|Llame a este método para obtener el texto que se muestra con el control.|
|[getvalid](#get_valid)|Llame a este método para obtener el estado de la marca que indica si el control es válido o no.|
|[get_Window](#get_window)|Llame a este método para obtener el identificador de ventana asociado con el control. Idéntico a [CStockPropImpl::get_HWND](#get_hwnd).|
|[put_Appearance](#put_appearance)|Llame a este método para establecer el estilo de pintura utilizado por el control, por ejemplo, plano o 3D.|
|[put_AutoSize](#put_autosize)|Llame a este método para establecer el valor de la marca que indica si el control no puede tener ningún otro tamaño.|
|[put_BackColor](#put_backcolor)|Llame a este método para establecer el color de fondo del control.|
|[put_BackStyle](#put_backstyle)|Llame a este método para establecer el estilo de fondo del control.|
|[put_BorderColor](#put_bordercolor)|Llame a este método para establecer el color del borde del control.|
|[put_BorderStyle](#put_borderstyle)|Llame a este método para establecer el estilo de borde del control.|
|[put_BorderVisible](#put_bordervisible)|Llame a este método para establecer el valor de la marca que indica si el borde del control es visible o no.|
|[put_BorderWidth](#put_borderwidth)|Llame a este método para establecer el ancho del borde del control.|
|[put_Caption](#put_caption)|Llame a este método para establecer el texto que se mostrará con el control.|
|[put_DrawMode](#put_drawmode)|Llame a este método para establecer el modo de dibujo del control, por ejemplo, XOR Pen o Invertir colores.|
|[put_DrawStyle](#put_drawstyle)|Llame a este método para establecer el estilo de dibujo del control, por ejemplo, sólido, discontinuo o punteado.|
|[put_DrawWidth](#put_drawwidth)|Llame a este método para establecer el ancho (en píxeles) utilizado por los métodos de dibujo del control.|
|[put_Enabled](#put_enabled)|Llame a este método para establecer el indicador que indica si el control está habilitado.|
|[put_FillColor](#put_fillcolor)|Llame a este método para establecer el color de relleno del control.|
|[put_FillStyle](#put_fillstyle)|Llame a este método para establecer el estilo de relleno del control, por ejemplo, sólido, transparente o rayado cruzado.|
|[put_Font](#put_font)|Llame a este método para establecer las propiedades de fuente del control.|
|[put_ForeColor](#put_forecolor)|Llame a este método para establecer el color de primer plano del control.|
|[put_HWND](#put_hwnd)|Este método devuelve E_FAIL.|
|[put_MouseIcon](#put_mouseicon)|Llame a este método para establecer las propiedades de imagen del gráfico (icono, mapa de bits o metarchivo) que se mostrará cuando el mouse está sobre el control.|
|[put_MousePointer](#put_mousepointer)|Llame a este método para establecer el tipo de puntero del mouse que se muestra cuando el mouse está sobre el control, por ejemplo, flecha, cruz o reloj de arena.|
|[put_Picture](#put_picture)|Llame a este método para establecer las propiedades de imagen de un gráfico (icono, mapa de bits o metarchivo) que se mostrará.|
|[put_ReadyState](#put_readystate)|Llame a este método para establecer el estado listo del control, por ejemplo, cargar o cargar.|
|[put_TabStop](#put_tabstop)|Llame a este método para establecer el valor de la marca que indica si el control es una tabulación o no.|
|[put_Text](#put_text)|Llame a este método para establecer el texto que se muestra con el control.|
|[putvalid](#put_valid)|Llame a este método para establecer el indicador que indica si el control es válido o no.|
|[put_Window](#put_window)|Este método llama a [CStockPropImpl::put_HWND](#put_hwnd), que devuelve E_FAIL.|
|[putref_Font](#putref_font)|Llame a este método para establecer las propiedades de fuente del control, con un recuento de referencias.|
|[putref_MouseIcon](#putref_mouseicon)|Llame a este método para establecer las propiedades de imagen del gráfico (icono, mapa de bits o metarchivo) que se mostrará cuando el mouse está sobre el control, con un recuento de referencias.|
|[putref_Picture](#putref_picture)|Llame a este método para establecer las propiedades de imagen de un gráfico (icono, mapa de bits o metarchivo) que se mostrará, con un recuento de referencias.|

## <a name="remarks"></a>Observaciones

`CStockPropImpl`proporciona métodos **put** y **get** para cada propiedad de stock. Estos métodos proporcionan el código necesario para establecer u obtener el miembro de datos asociado a cada propiedad y para notificar y sincronizar con el contenedor cuando cambia cualquier propiedad.

Visual Studio proporciona compatibilidad con las propiedades de stock a través de sus asistentes. Para obtener más información sobre cómo agregar propiedades de stock a un control, vea el [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md).

Por compatibilidad con `CStockPropImpl` versiones `get_Window` `put_Window` anteriores, `get_HWND` también `put_HWND`expone y métodos que simplemente llaman y , respectivamente. La implementación `put_HWND` predeterminada de devuelve E_FAIL ya que HWND debe ser una propiedad de solo lectura.

Las siguientes propiedades también tienen una implementación **putref:**

- Fuente

- MouseIcon

- Picture

Las mismas tres propiedades de stock requieren `CComPtr` que su miembro de datos correspondiente sea de tipo o de alguna otra clase que proporcione el recuento de referencias de interfaz correcto mediante el operador de asignación.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`T`

[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)

`CStockPropImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="cstockpropimplget_appearance"></a><a name="get_appearance"></a>CStockPropImpl::get_Appearance

Llame a este método para obtener el estilo de pintura utilizado por el control, por ejemplo, plano o 3D.

```
HRESULT STDMETHODCALLTYPE get_Appearance(SHORT pnAppearance);
```

### <a name="parameters"></a>Parámetros

*pnApariencia*<br/>
Variable que recibe el estilo de pintura del control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_autosize"></a><a name="get_autosize"></a>CStockPropImpl::get_AutoSize

Llame a este método para obtener el estado de la marca que indica si el control no puede ser de otro tamaño.

```
HRESULT STDMETHODCALLTYPE get_Autosize(VARIANT_BOOL* pbAutoSize);
```

### <a name="parameters"></a>Parámetros

*pbAutoSize*<br/>
Variable que recibe el estado de marca. TRUE indica que el control no puede tener ningún otro tamaño.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_backcolor"></a><a name="get_backcolor"></a>CStockPropImpl::get_BackColor

Llame a este método para obtener el color de fondo del control.

```
HRESULT STDMETHODCALLTYPE get_BackColor(OLE_COLOR* pclrBackColor);
```

### <a name="parameters"></a>Parámetros

*pclrBackColor*<br/>
Variable que recibe el color de fondo del control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_backstyle"></a><a name="get_backstyle"></a>CStockPropImpl::get_BackStyle

Llame a este método para obtener el estilo de fondo del control, transparente u opaco.

```
HRESULT STDMETHODCALLTYPE get_BackStyle(LONG* pnBackStyle);
```

### <a name="parameters"></a>Parámetros

*pnBackStyle*<br/>
Variable que recibe el estilo de fondo del control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_bordercolor"></a><a name="get_bordercolor"></a>CStockPropImpl::get_BorderColor

Llame a este método para obtener el color del borde del control.

```
HRESULT STDMETHODCALLTYPE get_BorderColor(OLE_COLOR* pclrBorderColor);
```

### <a name="parameters"></a>Parámetros

*pclrBorderColor*<br/>
Variable que recibe el color del borde del control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_borderstyle"></a><a name="get_borderstyle"></a>CStockPropImpl::get_BorderStyle

Llame a este método para obtener el estilo de borde del control.

```
HRESULT STDMETHODCALLTYPE get_BorderStyle(LONG* pnBorderStyle);
```

### <a name="parameters"></a>Parámetros

*pnBorderStyle*<br/>
Variable que recibe el estilo de borde del control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_bordervisible"></a><a name="get_bordervisible"></a>CStockPropImpl::get_BorderVisible

Llame a este método para obtener el estado de la marca que indica si el borde del control está visible o no.

```
HRESULT STDMETHODCALLTYPE get_BorderVisible(VARIANT_BOOL* pbBorderVisible);
```

### <a name="parameters"></a>Parámetros

*pbBorderVisible*<br/>
Variable que recibe el estado de marca. TRUE indica que el borde del control está visible.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_borderwidth"></a><a name="get_borderwidth"></a>CStockPropImpl::get_BorderWidth

Llame a este método para obtener el ancho del borde del control.

```
HRESULT STDMETHODCALLTYPE get_BorderWidth(LONG* pnBorderWidth);
```

### <a name="parameters"></a>Parámetros

*pnBorderWidth*<br/>
Variable que recibe el ancho del borde del control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_caption"></a><a name="get_caption"></a>CStockPropImpl::get_Caption

Llame a este método para obtener el texto especificado en el título de un objeto.

```
HRESULT STDMETHODCALLTYPE get_Caption(BSTR* pbstrCaption);
```

### <a name="parameters"></a>Parámetros

*pbstrCaption*<br/>
El texto que se mostrará con el control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_drawmode"></a><a name="get_drawmode"></a>CStockPropImpl::get_DrawMode

Llame a este método para obtener el modo de dibujo del control, por ejemplo, XOR Pen o Invertir colores.

```
HRESULT STDMETHODCALLTYPE get_DrawMode(LONG* pnDrawMode);
```

### <a name="parameters"></a>Parámetros

*pnDrawMode*<br/>
Variable que recibe el modo de dibujo del control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_drawstyle"></a><a name="get_drawstyle"></a>CStockPropImpl::get_DrawStyle

Llame a este método para obtener el estilo de dibujo del control, por ejemplo, sólido, discontinuo o punteado.

```
HRESULT STDMETHODCALLTYPE get_DrawStyle(LONG* pnDrawStyle);
```

### <a name="parameters"></a>Parámetros

*pnDrawStyle*<br/>
Variable que recibe el estilo de dibujo del control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_drawwidth"></a><a name="get_drawwidth"></a>CStockPropImpl::get_DrawWidth

Llame a este método para obtener el ancho del dibujo (en píxeles) utilizado por los métodos de dibujo del control.

```
HRESULT STDMETHODCALLTYPE get_DrawWidth(LONG* pnDrawWidth);
```

### <a name="parameters"></a>Parámetros

*pnDrawWidth*<br/>
Variable que recibe el valor de ancho del control, en píxeles.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_enabled"></a><a name="get_enabled"></a>CStockPropImpl::get_Enabled

Llame a este método para obtener el estado de la marca que indica si el control está habilitado.

```
HRESULT STDMETHODCALLTYPE get_Enabled(VARIANT_BOOL* pbEnabled);
```

### <a name="parameters"></a>Parámetros

*pbEnabled*<br/>
Variable que recibe el estado de marca. TRUE indica que el control está habilitado.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_fillcolor"></a><a name="get_fillcolor"></a>CStockPropImpl::get_FillColor

Llame a este método para obtener el color de relleno del control.

```
HRESULT STDMETHODCALLTYPE get_FillColor(OLE_COLOR* pclrFillColor);
```

### <a name="parameters"></a>Parámetros

*pclrFillColor*<br/>
Variable que recibe el color de relleno del control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_fillstyle"></a><a name="get_fillstyle"></a>CStockPropImpl::get_FillStyle

Llame a este método para obtener el estilo de relleno del control, por ejemplo, sólido, transparente o rayado.

```
HRESULT STDMETHODCALLTYPE get_FillStyle(LONG* pnFillStyle);
```

### <a name="parameters"></a>Parámetros

*pnFillStyle*<br/>
Variable que recibe el estilo de relleno del control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_font"></a><a name="get_font"></a>CStockPropImpl::get_Font

Llame a este método para obtener un puntero a las propiedades de fuente del control.

```
HRESULT STDMETHODCALLTYPE get_Font(IFontDisp** ppFont);
```

### <a name="parameters"></a>Parámetros

*ppFont*<br/>
Variable que recibe un puntero a las propiedades de fuente del control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_forecolor"></a><a name="get_forecolor"></a>CStockPropImpl::get_ForeColor

Llame a este método para obtener el color de primer plano del control.

```
HRESULT STDMETHODCALLTYPE get_ForeColor(OLE_COLOR* pclrForeColor);
```

### <a name="parameters"></a>Parámetros

*pclrForeColor*<br/>
Variable que recibe el color de primer plano de los controles.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_hwnd"></a><a name="get_hwnd"></a>CStockPropImpl::get_HWND

Llame a este método para obtener el identificador de ventana asociado con el control.

```
HRESULT STDMETHODCALLTYPE get_HWND(LONG_PTR* phWnd);
```

### <a name="parameters"></a>Parámetros

*phWnd*<br/>
Identificador de ventana asociado al control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_mouseicon"></a><a name="get_mouseicon"></a>CStockPropImpl::get_MouseIcon

Llame a este método para obtener las propiedades de imagen del gráfico (icono, mapa de bits o metarchivo) que se mostrará cuando el mouse está sobre el control.

```
HRESULT STDMETHODCALLTYPE get_MouseIcon(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>Parámetros

*ppPicture*<br/>
Variable que recibe un puntero a las propiedades de imagen del gráfico.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_mousepointer"></a><a name="get_mousepointer"></a>CStockPropImpl::get_MousePointer

Llame a este método para obtener el tipo de puntero del mouse que se muestra cuando el mouse está sobre el control, por ejemplo, flecha, cruz o reloj de arena.

```
HRESULT STDMETHODCALLTYPE get_MousePointer(LONG* pnMousePointer);
```

### <a name="parameters"></a>Parámetros

*pnMousePointer*<br/>
Variable que recibe el tipo de puntero del mouse.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_picture"></a><a name="get_picture"></a>CStockPropImpl::get_Picture

Llame a este método para obtener un puntero a las propiedades de imagen de un gráfico (icono, mapa de bits o metarchivo) que se va a mostrar.

```
HRESULT STDMETHODCALLTYPE get_Picture(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>Parámetros

*ppPicture*<br/>
Variable que recibe un puntero a las propiedades de la imagen. Consulte [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) para obtener más detalles.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_readystate"></a><a name="get_readystate"></a>CStockPropImpl::get_ReadyState

Llame a este método para obtener el estado listo del control, por ejemplo, cargar o cargar.

```
HRESULT STDMETHODCALLTYPE get_ReadyState(LONG* pnReadyState);
```

### <a name="parameters"></a>Parámetros

*pnReadyState*<br/>
Variable que recibe el estado listo del control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_tabstop"></a><a name="get_tabstop"></a>CStockPropImpl::get_TabStop

Llame a este método para obtener el estado de la marca que indica si el control es una tabulación o no.

```
HRESULT STDMETHODCALLTYPE get_TabStop(VARIANT_BOOL* pbTabStop);
```

### <a name="parameters"></a>Parámetros

*pbTabStop*<br/>
Variable que recibe el estado de marca. TRUE indica que el control es una tabulación.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_text"></a><a name="get_text"></a>CStockPropImpl::get_Text

Llame a este método para obtener el texto que se muestra con el control.

```
HRESULT STDMETHODCALLTYPE get_Text(BSTR* pbstrText);
```

### <a name="parameters"></a>Parámetros

*pbstrText*<br/>
El texto que se muestra con el control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplgetvalid"></a><a name="get_valid"></a>CStockPropImpl::getvalid

Llame a este método para obtener el estado de la marca que indica si el control es válido o no.

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL* pbValid);
```

### <a name="parameters"></a>Parámetros

*pbValid*<br/>
Variable que recibe el estado de marca. TRUE indica que el control es válido.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplget_window"></a><a name="get_window"></a>CStockPropImpl::get_Window

Llame a este método para obtener el identificador de ventana asociado con el control. Idéntico a [CStockPropImpl::get_HWND](#get_hwnd).

```
HRESULT STDMETHODCALLTYPE get_Window(LONG_PTR* phWnd);
```

### <a name="parameters"></a>Parámetros

*phWnd*<br/>
Identificador de ventana asociado al control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_appearance"></a><a name="put_appearance"></a>CStockPropImpl::put_Appearance

Llame a este método para establecer el estilo de pintura utilizado por el control, por ejemplo, plano o 3D.

```
HRESULT STDMETHODCALLTYPE put_Appearance(SHORT nAppearance);
```

### <a name="parameters"></a>Parámetros

*nApariencia*<br/>
El nuevo estilo de pintura que utilizará el control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_autosize"></a><a name="put_autosize"></a>CStockPropImpl::put_AutoSize

Llame a este método para establecer el valor de flag que indica si el control no puede tener ningún otro tamaño.

```
HRESULT STDMETHODCALLTYPE put_AutoSize(VARIANT_BOOL bAutoSize,);
```

### <a name="parameters"></a>Parámetros

*bAutoSize*<br/>
TRUESi el control no puede tener ningún otro tamaño.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_backcolor"></a><a name="put_backcolor"></a>CStockPropImpl::put_BackColor

Llame a este método para establecer el color de fondo del control.

```
HRESULT STDMETHODCALLTYPE put_BackColor(OLE_COLOR clrBackColor);
```

### <a name="parameters"></a>Parámetros

*clrBackColor*<br/>
El nuevo color de fondo de control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_backstyle"></a><a name="put_backstyle"></a>CStockPropImpl::put_BackStyle

Llame a este método para establecer el estilo de fondo del control.

```
HRESULT STDMETHODCALLTYPE put_BackStyle(LONG nBackStyle);
```

### <a name="parameters"></a>Parámetros

*nBackStyle*<br/>
El nuevo estilo de fondo de control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_bordercolor"></a><a name="put_bordercolor"></a>CStockPropImpl::put_BorderColor

Llame a este método para establecer el color del borde del control.

```
HRESULT STDMETHODCALLTYPE put_BorderColor(OLE_COLOR clrBorderColor);
```

### <a name="parameters"></a>Parámetros

*clrBorderColor*<br/>
El nuevo color del borde. El tipo de datos OLE_COLOR se representa internamente como un entero largo de 32 bits.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_borderstyle"></a><a name="put_borderstyle"></a>CStockPropImpl::put_BorderStyle

Llame a este método para establecer el estilo de borde del control.

```
HRESULT STDMETHODCALLTYPE put_BorderStyle(LONG nBorderStyle);
```

### <a name="parameters"></a>Parámetros

*nBorderStyle*<br/>
El nuevo estilo de borde.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_bordervisible"></a><a name="put_bordervisible"></a>CStockPropImpl::put_BorderVisible

Llame a este método para establecer el valor de la marca que indica si el borde del control es visible o no.

```
HRESULT STDMETHODCALLTYPE put_BorderVisible(VARIANT_BOOL bBorderVisible);
```

### <a name="parameters"></a>Parámetros

*bBorderVisible*<br/>
TRUESi el borde va a ser visible.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_borderwidth"></a><a name="put_borderwidth"></a>CStockPropImpl::put_BorderWidth

Llame a este método para establecer el ancho del borde del control.

```
HRESULT STDMETHODCALLTYPE put_BorderWidth(LONG nBorderWidth);
```

### <a name="parameters"></a>Parámetros

*nBorderWidth*<br/>
El nuevo ancho del borde del control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_caption"></a><a name="put_caption"></a>CStockPropImpl::put_Caption

Llame a este método para establecer el texto que se mostrará con el control.

```
HRESULT STDMETHODCALLTYPE put_Caption(BSTR bstrCaption);
```

### <a name="parameters"></a>Parámetros

*bstrCaption*<br/>
El texto que se mostrará con el control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_drawmode"></a><a name="put_drawmode"></a>CStockPropImpl::put_DrawMode

Llame a este método para establecer el modo de dibujo del control, por ejemplo, XOR Pen o Invertir colores.

```
HRESULT STDMETHODCALLTYPE put_DrawMode(LONG nDrawMode);
```

### <a name="parameters"></a>Parámetros

*nDrawMode*<br/>
El nuevo modo de dibujo para el control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_drawstyle"></a><a name="put_drawstyle"></a>CStockPropImpl::put_DrawStyle

Llame a este método para establecer el estilo de dibujo del control, por ejemplo, sólido, discontinuo o punteado.

```
HRESULT STDMETHODCALLTYPE put_DrawStyle(LONG pnDrawStyle);
```

### <a name="parameters"></a>Parámetros

*nDrawStyle*<br/>
El nuevo estilo de dibujo para el control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_drawwidth"></a><a name="put_drawwidth"></a>CStockPropImpl::put_DrawWidth

Llame a este método para establecer el ancho (en píxeles) utilizado por los métodos de dibujo del control.

```
HRESULT STDMETHODCALLTYPE put_DrawWidth(LONG nDrawWidth);
```

### <a name="parameters"></a>Parámetros

*nDrawWidth*<br/>
El nuevo ancho que utilizarán los métodos de dibujo del control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_enabled"></a><a name="put_enabled"></a>CStockPropImpl::put_Enabled

Llame a este método para establecer el valor de la marca que indica si el control está habilitado.

```
HRESULT STDMETHODCALLTYPE put_Enabled(VARIANT_BOOL bEnabled);
```

### <a name="parameters"></a>Parámetros

*bHabilitado*<br/>
TRUESi el control está habilitado.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_fillcolor"></a><a name="put_fillcolor"></a>CStockPropImpl::put_FillColor

Llame a este método para establecer el color de relleno del control.

```
HRESULT STDMETHODCALLTYPE put_FillColor(OLE_COLOR clrFillColor);
```

### <a name="parameters"></a>Parámetros

*clrFillColor*<br/>
El nuevo color de relleno para el control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_fillstyle"></a><a name="put_fillstyle"></a>CStockPropImpl::put_FillStyle

Llame a este método para establecer el estilo de relleno del control, por ejemplo, sólido, transparente o rayado cruzado.

```
HRESULT STDMETHODCALLTYPE put_FillStyle(LONG nFillStyle);
```

### <a name="parameters"></a>Parámetros

*nFillStyle*<br/>
El nuevo estilo de relleno para el control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_font"></a><a name="put_font"></a>CStockPropImpl::put_Font

Llame a este método para establecer las propiedades de fuente del control.

```
HRESULT STDMETHODCALLTYPE put_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>Parámetros

*pFont*<br/>
Un puntero a las propiedades de fuente del control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_forecolor"></a><a name="put_forecolor"></a>CStockPropImpl::put_ForeColor

Llame a este método para establecer el color de primer plano del control.

```
HRESULT STDMETHODCALLTYPE put_ForeColor(OLE_COLOR clrForeColor);
```

### <a name="parameters"></a>Parámetros

*clrForeColor*<br/>
El nuevo color de primer plano del control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_hwnd"></a><a name="put_hwnd"></a>CStockPropImpl::put_HWND

Este método devuelve E_FAIL.

```
HRESULT STDMETHODCALLTYPE put_HWND(LONG_PTR /* hWnd */);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
Reservado.

### <a name="return-value"></a>Valor devuelto

Devuelve E_FAIL.

### <a name="remarks"></a>Observaciones

El identificador de ventana es un valor de solo lectura.

## <a name="cstockpropimplput_mouseicon"></a><a name="put_mouseicon"></a>CStockPropImpl::put_MouseIcon

Llame a este método para establecer las propiedades de imagen del gráfico (icono, mapa de bits o metarchivo) que se mostrará cuando el mouse está sobre el control.

```
HRESULT STDMETHODCALLTYPE put_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parámetros

*pPicture*<br/>
Un puntero a las propiedades de imagen del gráfico.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_mousepointer"></a><a name="put_mousepointer"></a>CStockPropImpl::put_MousePointer

Llame a este método para establecer el tipo de puntero del mouse que se muestra cuando el mouse está sobre el control, por ejemplo, flecha, cruz o reloj de arena.

```
HRESULT STDMETHODCALLTYPE put_MousePointer(LONG nMousePointer);
```

### <a name="parameters"></a>Parámetros

*nMousePointer*<br/>
El tipo de puntero del mouse.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_picture"></a><a name="put_picture"></a>CStockPropImpl::put_Picture

Llame a este método para establecer las propiedades de imagen de un gráfico (icono, mapa de bits o metarchivo) que se mostrará.

```
HRESULT STDMETHODCALLTYPE put_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parámetros

*pPicture*<br/>
Un puntero a las propiedades de la imagen. Consulte [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) para obtener más detalles.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_readystate"></a><a name="put_readystate"></a>CStockPropImpl::put_ReadyState

Llame a este método para establecer el estado listo del control, por ejemplo, cargar o cargar.

```
HRESULT STDMETHODCALLTYPE put_ReadyState(LONG nReadyState);
```

### <a name="parameters"></a>Parámetros

*nReadyState*<br/>
El control está listo.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_tabstop"></a><a name="put_tabstop"></a>CStockPropImpl::put_TabStop

Llame a este método para establecer el indicador que indica si el control es una tabulación o no.

```
HRESULT STDMETHODCALLTYPE put_TabStop(VARIANT_BOOL bTabStop);
```

### <a name="parameters"></a>Parámetros

*bTabStop*<br/>
TRUESi el control es una tabulación.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_text"></a><a name="put_text"></a>CStockPropImpl::put_Text

Llame a este método para establecer el texto que se muestra con el control.

```
HRESULT STDMETHODCALLTYPE put_Text(BSTR bstrText);
```

### <a name="parameters"></a>Parámetros

*bstrText*<br/>
El texto que se muestra con el control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplputvalid"></a><a name="put_valid"></a>CStockPropImpl::putvalid

Llame a este método para establecer el indicador que indica si el control es válido o no.

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL bValid);
```

### <a name="parameters"></a>Parámetros

*bVálido*<br/>
TRUESi el control es válido.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cstockpropimplput_window"></a><a name="put_window"></a>CStockPropImpl::put_Window

Este método llama a [CStockPropImpl::put_HWND](#put_hwnd), que devuelve E_FAIL.

```
HRESULT STDMETHODCALLTYPE put_Window(LONG_PTR hWnd);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
Identificador de la ventana.

### <a name="return-value"></a>Valor devuelto

Devuelve E_FAIL.

### <a name="remarks"></a>Observaciones

El identificador de ventana es un valor de solo lectura.

## <a name="cstockpropimplputref_font"></a><a name="putref_font"></a>CStockPropImpl::putref_Font

Llame a este método para establecer las propiedades de fuente del control, con un recuento de referencias.

```
HRESULT STDMETHODCALLTYPE putref_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>Parámetros

*pFont*<br/>
Un puntero a las propiedades de fuente del control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Lo mismo que [CStockPropImpl::put_Font](#put_font), pero con un recuento de referencias.

## <a name="cstockpropimplputref_mouseicon"></a><a name="putref_mouseicon"></a>CStockPropImpl::putref_MouseIcon

Llame a este método para establecer las propiedades de imagen del gráfico (icono, mapa de bits o metarchivo) que se mostrará cuando el mouse está sobre el control, con un recuento de referencias.

```
HRESULT STDMETHODCALLTYPE putref_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parámetros

*pPicture*<br/>
Un puntero a las propiedades de imagen del gráfico.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Lo mismo que [CStockPropImpl::put_MouseIcon](#put_mouseicon), pero con un recuento de referencias.

## <a name="cstockpropimplputref_picture"></a><a name="putref_picture"></a>CStockPropImpl::putref_Picture

Llame a este método para establecer las propiedades de imagen de un gráfico (icono, mapa de bits o metarchivo) que se mostrará, con un recuento de referencias.

```
HRESULT STDMETHODCALLTYPE putref_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parámetros

*pPicture*<br/>
Un puntero a las propiedades de la imagen. Consulte [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) para obtener más detalles.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Lo mismo que [CStockPropImpl::put_Picture](#put_picture), pero con un recuento de referencias.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clase IDispatchImpl](../../atl/reference/idispatchimpl-class.md)
