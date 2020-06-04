---
title: Interfaz IAxWinAmbientDispatch
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatch
- ATLIFACE/ATL::IAxWinAmbientDispatch
- ATLIFACE/ATL::get_AllowContextMenu
- ATLIFACE/ATL::get_AllowShowUI
- ATLIFACE/ATL::get_AllowWindowlessActivation
- ATLIFACE/ATL::get_BackColor
- ATLIFACE/ATL::get_DisplayAsDefault
- ATLIFACE/ATL::get_DocHostDoubleClickFlags
- ATLIFACE/ATL::get_DocHostFlags
- ATLIFACE/ATL::get_Font
- ATLIFACE/ATL::get_ForeColor
- ATLIFACE/ATL::get_LocaleID
- ATLIFACE/ATL::get_MessageReflect
- ATLIFACE/ATL::get_OptionKeyPath
- ATLIFACE/ATL::get_ShowGrabHandles
- ATLIFACE/ATL::get_ShowHatching
- ATLIFACE/ATL::get_UserMode
- ATLIFACE/ATL::put_AllowContextMenu
- ATLIFACE/ATL::put_AllowShowUI
- ATLIFACE/ATL::put_AllowWindowlessActivation
- ATLIFACE/ATL::put_BackColor
- ATLIFACE/ATL::put_DisplayAsDefault
- ATLIFACE/ATL::put_DocHostDoubleClickFlags
- ATLIFACE/ATL::put_DocHostFlags
- ATLIFACE/ATL::put_Font
- ATLIFACE/ATL::put_ForeColor
- ATLIFACE/ATL::put_LocaleID
- ATLIFACE/ATL::put_MessageReflect
- ATLIFACE/ATL::put_OptionKeyPath
- ATLIFACE/ATL::put_UserMode
helpviewer_keywords:
- IAxWinAmbientDispatch interface
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
ms.openlocfilehash: 6a4f5322d957b1e978bd123db3b4796be6b300da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330006"
---
# <a name="iaxwinambientdispatch-interface"></a>Interfaz IAxWinAmbientDispatch

Esta interfaz proporciona métodos para especificar las características del control hospedado o contenedor.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
interface IAxWinAmbientDispatch : IDispatch
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[get_AllowContextMenu](#get_allowcontextmenu)|La `AllowContextMenu` propiedad especifica si el control hospedado puede mostrar su propio menú contextual.|
|[get_AllowShowUI](#get_allowshowui)|La `AllowShowUI` propiedad especifica si el control hospedado puede mostrar su propia interfaz de usuario.|
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|La `AllowWindowlessActivation` propiedad especifica si el contenedor permitirá la activación sin ventanas.|
|[get_BackColor](#get_backcolor)|La `BackColor` propiedad especifica el color de fondo ambiente del contenedor.|
|[get_DisplayAsDefault](#get_displayasdefault)|`DisplayAsDefault`es una propiedad ambiente que permite a un control averiguar si es el control predeterminado.|
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|La `DocHostDoubleClickFlags` propiedad especifica la operación que debe tener lugar en respuesta a un doble clic.|
|[get_DocHostFlags](#get_dochostflags)|La `DocHostFlags` propiedad especifica las capacidades de la interfaz de usuario del objeto host.|
|[get_Font](#get_font)|La `Font` propiedad especifica la fuente ambiente del contenedor.|
|[get_ForeColor](#get_forecolor)|La `ForeColor` propiedad especifica el color de primer plano ambiente del contenedor.|
|[get_LocaleID](#get_localeid)|La `LocaleID` propiedad especifica el identificador de configuración regional ambiente del contenedor.|
|[get_MessageReflect](#get_messagereflect)|La `MessageReflect` propiedad ambient especifica si el contenedor reflejará los mensajes en el control hospedado.|
|[get_OptionKeyPath](#get_optionkeypath)|La `OptionKeyPath` propiedad especifica la ruta de acceso de la clave del Registro a la configuración de usuario.|
|[get_ShowGrabHandles](#get_showgrabhandles)|La `ShowGrabHandles` propiedad ambiente permite que el control averiguar si debe dibujarse con asas de agarre.|
|[get_ShowHatching](#get_showhatching)|La `ShowHatching` propiedad ambient permite al control averiguar si debe dibujarse sombreado.|
|[get_UserMode](#get_usermode)|La `UserMode` propiedad especifica el modo de usuario ambiente del contenedor.|
|[put_AllowContextMenu](#put_allowcontextmenu)|La `AllowContextMenu` propiedad especifica si el control hospedado puede mostrar su propio menú contextual.|
|[put_AllowShowUI](#put_allowshowui)|La `AllowShowUI` propiedad especifica si el control hospedado puede mostrar su propia interfaz de usuario.|
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|La `AllowWindowlessActivation` propiedad especifica si el contenedor permitirá la activación sin ventanas.|
|[put_BackColor](#put_backcolor)|La `BackColor` propiedad especifica el color de fondo ambiente del contenedor.|
|[put_DisplayAsDefault](#put_displayasdefault)|`DisplayAsDefault`es una propiedad ambiente que permite a un control averiguar si es el control predeterminado.|
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|La `DocHostDoubleClickFlags` propiedad especifica la operación que debe tener lugar en respuesta a un doble clic.|
|[put_DocHostFlags](#put_dochostflags)|La `DocHostFlags` propiedad especifica las capacidades de la interfaz de usuario del objeto host.|
|[put_Font](#put_font)|La `Font` propiedad especifica la fuente ambiente del contenedor.|
|[put_ForeColor](#put_forecolor)|La `ForeColor` propiedad especifica el color de primer plano ambiente del contenedor.|
|[put_LocaleID](#put_localeid)|La `LocaleID` propiedad especifica el identificador de configuración regional ambiente del contenedor.|
|[put_MessageReflect](#put_messagereflect)|La `MessageReflect` propiedad ambient especifica si el contenedor reflejará los mensajes en el control hospedado.|
|[put_OptionKeyPath](#put_optionkeypath)|La `OptionKeyPath` propiedad especifica la ruta de acceso de la clave del Registro a la configuración de usuario.|
|[put_UserMode](#put_usermode)|La `UserMode` propiedad especifica el modo de usuario ambiente del contenedor.|

## <a name="remarks"></a>Observaciones

Esta interfaz se expone mediante objetos de hospedaje de control ActiveX de ATL. Llame a los métodos de esta interfaz para establecer las propiedades ambientales disponibles para el control hospedado o para especificar otros aspectos del comportamiento del contenedor. Para complementar las `IAxWinAmbientDispatch`propiedades proporcionadas por , use [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md).

<xref:System.Windows.Forms.AxHost>intentará cargar información de `IAxWinAmbientDispatch` `IAxWinAmbientDispatchEx` tipo sobre y desde la biblioteca de tipos que contiene el código.

Si está vinculando a ATL90.dll, **AXHost** cargará la información de tipo de la biblioteca de tipos en el archivo DLL.

Consulte [Hosting ActiveX Controls Using ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener más detalles.

## <a name="requirements"></a>Requisitos

La definición de esta interfaz está disponible en una serie de formas, como se muestra en la tabla siguiente.

|Tipo de definición|Archivo|
|---------------------|----------|
|Idl|atliface.idl|
|Biblioteca de tipos|Atl.dll|
|C++|atliface.h (también incluido en ATLBase.h)|

## <a name="iaxwinambientdispatchget_allowcontextmenu"></a><a name="get_allowcontextmenu"></a>IAxWinAmbientDispatch::get_AllowContextMenu

La `AllowContextMenu` propiedad especifica si el control hospedado puede mostrar su propio menú contextual.

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>Parámetros

*pbAllowContextMenu*<br/>
[fuera] La dirección de una variable para recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza VARIANT_TRUE como valor predeterminado de esta propiedad.

## <a name="iaxwinambientdispatchget_allowshowui"></a><a name="get_allowshowui"></a>IAxWinAmbientDispatch::get_AllowShowUI

La `AllowShowUI` propiedad especifica si el control hospedado puede mostrar su propia interfaz de usuario.

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>Parámetros

*pbAllowShowUI*<br/>
[fuera] La dirección de una variable para recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza VARIANT_FALSE como valor predeterminado de esta propiedad.

## <a name="iaxwinambientdispatchget_allowwindowlessactivation"></a><a name="get_allowwindowlessactivation"></a>IAxWinAmbientDispatch::get_AllowWindowlessActivation

La `AllowWindowlessActivation` propiedad especifica si el contenedor permitirá la activación sin ventanas.

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>Parámetros

*pbAllowWindowless*<br/>
[fuera] La dirección de una variable para recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza VARIANT_TRUE como valor predeterminado de esta propiedad.

## <a name="iaxwinambientdispatchget_backcolor"></a><a name="get_backcolor"></a>IAxWinAmbientDispatch::get_BackColor

La `BackColor` propiedad especifica el color de fondo ambiente del contenedor.

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>Parámetros

*pclrBackground*<br/>
[fuera] La dirección de una variable para recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza COLOR_BTNFACE o COLOR_WINDOW como valor predeterminado de esta propiedad (dependiendo de si el elemento primario de la ventana host es un cuadro de diálogo o no).

## <a name="iaxwinambientdispatchget_displayasdefault"></a><a name="get_displayasdefault"></a>IAxWinAmbientDispatch::get_DisplayAsDefault

`DisplayAsDefault`es una propiedad ambiente que permite a un control averiguar si es el control predeterminado.

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>Parámetros

*pbDisplayAsDefault*<br/>
[fuera] La dirección de una variable para recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza VARIANT_FALSE como valor predeterminado de esta propiedad.

## <a name="iaxwinambientdispatchget_dochostdoubleclickflags"></a><a name="get_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::get_DocHostDoubleClickFlags

La `DocHostDoubleClickFlags` propiedad especifica la operación que debe tener lugar en respuesta a un doble clic.

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parámetros

*pdwDocHostDoubleClickFlags*<br/>
[fuera] La dirección de una variable para recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza DOCHOSTUIDBLCLK_DEFAULT como valor predeterminado de esta propiedad.

## <a name="iaxwinambientdispatchget_dochostflags"></a><a name="get_dochostflags"></a>IAxWinAmbientDispatch::get_DocHostFlags

La `DocHostFlags` propiedad especifica las capacidades de la interfaz de usuario del objeto host.

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>Parámetros

*pdwDocHostFlags*<br/>
[fuera] La dirección de una variable para recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza DOCHOSTUIFLAG_NO3DBORDER como valor predeterminado de esta propiedad.

## <a name="iaxwinambientdispatchget_font"></a><a name="get_font"></a>IAxWinAmbientDispatch::get_Font

La `Font` propiedad especifica la fuente ambiente del contenedor.

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>Parámetros

*pFont*<br/>
[fuera] La dirección `IFontDisp` de un puntero de interfaz utilizado para recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza la fuente GUI predeterminada o la fuente del sistema como valor predeterminado de esta propiedad.

## <a name="iaxwinambientdispatchget_forecolor"></a><a name="get_forecolor"></a>IAxWinAmbientDispatch::get_ForeColor

La `ForeColor` propiedad especifica el color de primer plano ambiente del contenedor.

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>Parámetros

*pclrForeground*<br/>
[fuera] La dirección de una variable para recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza el color de texto de la ventana del sistema como valor predeterminado de esta propiedad.

## <a name="iaxwinambientdispatchget_localeid"></a><a name="get_localeid"></a>IAxWinAmbientDispatch::get_LocaleID

La `LocaleID` propiedad especifica el identificador de configuración regional ambiente del contenedor.

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>Parámetros

*plcidLocaleID*<br/>
[fuera] La dirección de una variable para recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza la configuración regional predeterminada del usuario como valor predeterminado de esta propiedad.

Con este método puede descubrir el Ambient LocalID, es decir, el LocaleID del programa en el que se utiliza el control. Una vez que conozca el LocaleID, puede llamar al código para cargar subtítulos específicos de la configuración regional, texto del mensaje de error, etc. desde un archivo de recursos o DLL satélite.

## <a name="iaxwinambientdispatchget_messagereflect"></a><a name="get_messagereflect"></a>IAxWinAmbientDispatch::get_MessageReflect

La `MessageReflect` propiedad ambient especifica si el contenedor reflejará los mensajes en el control hospedado.

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>Parámetros

*pbMessageReflect*<br/>
[fuera] La dirección de una variable para recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza VARIANT_TRUE como valor predeterminado de esta propiedad.

## <a name="iaxwinambientdispatchget_optionkeypath"></a><a name="get_optionkeypath"></a>IAxWinAmbientDispatch::get_OptionKeyPath

La `OptionKeyPath` propiedad especifica la ruta de acceso de la clave del Registro a la configuración de usuario.

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>Parámetros

*pbstrOptionKeyPath*<br/>
[fuera] La dirección de una variable para recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="iaxwinambientdispatchget_showgrabhandles"></a><a name="get_showgrabhandles"></a>IAxWinAmbientDispatch::get_ShowGrabHandles

La `ShowGrabHandles` propiedad ambiente permite que el control averiguar si debe dibujarse con asas de agarre.

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>Parámetros

*pbShowGrabHandles*<br/>
[fuera] La dirección de una variable para recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL siempre devuelve VARIANT_FALSE como el valor de esta propiedad.

## <a name="iaxwinambientdispatchget_showhatching"></a><a name="get_showhatching"></a>IAxWinAmbientDispatch::get_ShowHatching

La `ShowHatching` propiedad ambient permite al control averiguar si debe dibujarse sombreado.

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>Parámetros

*pbShowHatching*<br/>
[fuera] La dirección de una variable para recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL siempre devuelve VARIANT_FALSE como el valor de esta propiedad.

## <a name="iaxwinambientdispatchget_usermode"></a><a name="get_usermode"></a>IAxWinAmbientDispatch::get_UserMode

La `UserMode` propiedad especifica el modo de usuario ambiente del contenedor.

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>Parámetros

*pbUserMode*<br/>
[fuera] La dirección de una variable para recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza VARIANT_TRUE como valor predeterminado de esta propiedad.

## <a name="iaxwinambientdispatchput_allowcontextmenu"></a><a name="put_allowcontextmenu"></a>IAxWinAmbientDispatch::put_AllowContextMenu

La `AllowContextMenu` propiedad especifica si el control hospedado puede mostrar su propio menú contextual.

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>Parámetros

*bAllowContextMenu*<br/>
[en] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza VARIANT_TRUE como valor predeterminado de esta propiedad.

## <a name="iaxwinambientdispatchput_allowshowui"></a><a name="put_allowshowui"></a>IAxWinAmbientDispatch::put_AllowShowUI

La `AllowShowUI` propiedad especifica si el control hospedado puede mostrar su propia interfaz de usuario.

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>Parámetros

*bAllowShowUI*<br/>
[en] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza VARIANT_FALSE como valor predeterminado de esta propiedad.

## <a name="iaxwinambientdispatchput_allowwindowlessactivation"></a><a name="put_allowwindowlessactivation"></a>IAxWinAmbientDispatch::put_AllowWindowlessActivation

La `AllowWindowlessActivation` propiedad especifica si el contenedor permitirá la activación sin ventanas.

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>Parámetros

*bAllowWindowless*<br/>
[en] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza VARIANT_TRUE como valor predeterminado de esta propiedad.

## <a name="iaxwinambientdispatchput_backcolor"></a><a name="put_backcolor"></a>IAxWinAmbientDispatch::put_BackColor

La `BackColor` propiedad especifica el color de fondo ambiente del contenedor.

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>Parámetros

*clrBackground*<br/>
[en] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza COLOR_BTNFACE o COLOR_WINDOW como valor predeterminado de esta propiedad (dependiendo de si el elemento primario de la ventana host es un cuadro de diálogo o no).

## <a name="iaxwinambientdispatchput_displayasdefault"></a><a name="put_displayasdefault"></a>IAxWinAmbientDispatch::put_DisplayAsDefault

`DisplayAsDefault`es una propiedad ambiente que permite a un control averiguar si es el control predeterminado.

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>Parámetros

*bDisplayAsDefault*<br/>
[en] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza VARIANT_FALSE como valor predeterminado de esta propiedad.

## <a name="iaxwinambientdispatchput_dochostdoubleclickflags"></a><a name="put_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::put_DocHostDoubleClickFlags

La `DocHostDoubleClickFlags` propiedad especifica la operación que debe tener lugar en respuesta a un doble clic.

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parámetros

*dwDocHostDoubleClickFlags*<br/>
[en] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza DOCHOSTUIDBLCLK_DEFAULT como valor predeterminado de esta propiedad.

## <a name="iaxwinambientdispatchput_dochostflags"></a><a name="put_dochostflags"></a>IAxWinAmbientDispatch::put_DocHostFlags

La `DocHostFlags` propiedad especifica las capacidades de la interfaz de usuario del objeto host.

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>Parámetros

*dwDocHostFlags*<br/>
[en] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza DOCHOSTUIFLAG_NO3DBORDER como valor predeterminado de esta propiedad.

## <a name="iaxwinambientdispatchput_font"></a><a name="put_font"></a>IAxWinAmbientDispatch::put_Font

La `Font` propiedad especifica la fuente ambiente del contenedor.

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>Parámetros

*pFont*<br/>
[en] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza la fuente GUI predeterminada o la fuente del sistema como valor predeterminado de esta propiedad.

## <a name="iaxwinambientdispatchput_forecolor"></a><a name="put_forecolor"></a>IAxWinAmbientDispatch::put_ForeColor

La `ForeColor` propiedad especifica el color de primer plano ambiente del contenedor.

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>Parámetros

*clrForeground*<br/>
[en] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza el color de texto de la ventana del sistema como valor predeterminado de esta propiedad.

## <a name="iaxwinambientdispatchput_localeid"></a><a name="put_localeid"></a>IAxWinAmbientDispatch::put_LocaleID

La `LocaleID` propiedad especifica el identificador de configuración regional ambiente del contenedor.

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>Parámetros

*lcidLocaleID*<br/>
[en] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza la configuración regional predeterminada del usuario como valor predeterminado de esta propiedad.

## <a name="iaxwinambientdispatchput_messagereflect"></a><a name="put_messagereflect"></a>IAxWinAmbientDispatch::put_MessageReflect

La `MessageReflect` propiedad ambient especifica si el contenedor reflejará los mensajes en el control hospedado.

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>Parámetros

*bMessageReflect*<br/>
[en] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza VARIANT_TRUE como valor predeterminado de esta propiedad.

## <a name="iaxwinambientdispatchput_optionkeypath"></a><a name="put_optionkeypath"></a>IAxWinAmbientDispatch::put_OptionKeyPath

La `OptionKeyPath` propiedad especifica la ruta de acceso de la clave del Registro a la configuración de usuario.

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>Parámetros

*bstrOptionKeyPath*<br/>
[en] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="iaxwinambientdispatchput_usermode"></a><a name="put_usermode"></a>IAxWinAmbientDispatch::put_UserMode

La `UserMode` propiedad especifica el modo de usuario ambiente del contenedor.

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>Parámetros

*bUserMode*<br/>
[en] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación del objeto host ATL utiliza VARIANT_TRUE como valor predeterminado de esta propiedad.

## <a name="see-also"></a>Consulte también

[Interfaz IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)<br/>
[Interfaz IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
