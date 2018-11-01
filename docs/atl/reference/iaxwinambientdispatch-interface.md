---
title: IAxWinAmbientDispatch (interfaz)
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
ms.openlocfilehash: f143b2c58159d1bb0812152c68d3c31153d4570d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467436"
---
# <a name="iaxwinambientdispatch-interface"></a>IAxWinAmbientDispatch (interfaz)

Esta interfaz proporciona métodos para especificar las características del control hospedado o contenedor.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
interface IAxWinAmbientDispatch : IDispatch
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[get_AllowContextMenu](#get_allowcontextmenu)|El `AllowContextMenu` propiedad especifica si el control hospedado se puede mostrar su propio menú contextual.|
|[get_AllowShowUI](#get_allowshowui)|El `AllowShowUI` propiedad especifica si el control hospedado se puede mostrar su propia interfaz de usuario.|
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|El `AllowWindowlessActivation` propiedad especifica si el contenedor permitirá la activación sin ventana.|
|[get_BackColor](#get_backcolor)|El `BackColor` propiedad especifica el color de fondo de ambiente del contenedor.|
|[get_DisplayAsDefault](#get_displayasdefault)|`DisplayAsDefault` es una propiedad de ambiente que permite un control averiguar si es el control predeterminado.|
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|El `DocHostDoubleClickFlags` propiedad especifica la operación que se debe llevar a cabo en respuesta a un doble clic.|
|[get_DocHostFlags](#get_dochostflags)|El `DocHostFlags` propiedad especifica las capacidades de la interfaz de usuario del objeto host.|
|[get_Font](#get_font)|El `Font` propiedad especifica la fuente de ambiente del contenedor.|
|[get_ForeColor](#get_forecolor)|El `ForeColor` propiedad especifica el color de primer plano ambiente del contenedor.|
|[get_LocaleID](#get_localeid)|El `LocaleID` propiedad especifica el identificador de configuración regional de ambiente del contenedor.|
|[get_MessageReflect](#get_messagereflect)|El `MessageReflect` propiedad ambiente especifica si el contenedor reflejará los mensajes para el control hospedado.|
|[get_OptionKeyPath](#get_optionkeypath)|El `OptionKeyPath` propiedad especifica la ruta de acceso de clave del registro a la configuración de usuario.|
|[get_ShowGrabHandles](#get_showgrabhandles)|El `ShowGrabHandles` propiedad ambiente permite que el control averiguar si debe dibujar con controladores de arrastre.|
|[get_ShowHatching](#get_showhatching)|El `ShowHatching` propiedad ambiente permite que el control averiguar si debe dibujarse a sí mismo sombreada.|
|[get_UserMode](#get_usermode)|El `UserMode` propiedad especifica el modo de usuario de ambiente del contenedor.|
|[put_AllowContextMenu](#put_allowcontextmenu)|El `AllowContextMenu` propiedad especifica si el control hospedado se puede mostrar su propio menú contextual.|
|[put_AllowShowUI](#put_allowshowui)|El `AllowShowUI` propiedad especifica si el control hospedado se puede mostrar su propia interfaz de usuario.|
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|El `AllowWindowlessActivation` propiedad especifica si el contenedor permitirá la activación sin ventana.|
|[put_BackColor](#put_backcolor)|El `BackColor` propiedad especifica el color de fondo de ambiente del contenedor.|
|[put_DisplayAsDefault](#put_displayasdefault)|`DisplayAsDefault` es una propiedad de ambiente que permite un control averiguar si es el control predeterminado.|
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|El `DocHostDoubleClickFlags` propiedad especifica la operación que se debe llevar a cabo en respuesta a un doble clic.|
|[put_DocHostFlags](#put_dochostflags)|El `DocHostFlags` propiedad especifica las capacidades de la interfaz de usuario del objeto host.|
|[put_Font](#put_font)|El `Font` propiedad especifica la fuente de ambiente del contenedor.|
|[put_ForeColor](#put_forecolor)|El `ForeColor` propiedad especifica el color de primer plano ambiente del contenedor.|
|[put_LocaleID](#put_localeid)|El `LocaleID` propiedad especifica el identificador de configuración regional de ambiente del contenedor.|
|[put_MessageReflect](#put_messagereflect)|El `MessageReflect` propiedad ambiente especifica si el contenedor reflejará los mensajes para el control hospedado.|
|[put_OptionKeyPath](#put_optionkeypath)|El `OptionKeyPath` propiedad especifica la ruta de acceso de clave del registro a la configuración de usuario.|
|[put_UserMode](#put_usermode)|El `UserMode` propiedad especifica el modo de usuario de ambiente del contenedor.|

## <a name="remarks"></a>Comentarios

Esta interfaz se expone mediante los objetos que hospeda los controles ActiveX de ATL. Llamar a los métodos de esta interfaz para establecer las propiedades de ambientales disponibles en el control hospedado o para especificar otros aspectos del comportamiento del contenedor. Para complementar las propiedades proporcionadas por `IAxWinAmbientDispatch`, utilice [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md).

[AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx) intentará cargar la información de tipo sobre `IAxWinAmbientDispatch` y `IAxWinAmbientDispatchEx` desde la biblioteca de tipos que contiene el código.

Si vincula a ATL90.dll, **AXHost** cargará la información de tipo de la biblioteca de tipos en el archivo DLL.

Consulte [hospeda controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener más detalles.

## <a name="requirements"></a>Requisitos

La definición de esta interfaz está disponible en varios formatos, como se muestra en la tabla siguiente.

|Tipo de definición|Archivo|
|---------------------|----------|
|IDL|atliface.idl|
|Biblioteca de tipos|ATL.dll|
|C++|atliface.h (que también se incluye en ATLBase.h)|

##  <a name="get_allowcontextmenu"></a>  IAxWinAmbientDispatch::get_AllowContextMenu

El `AllowContextMenu` propiedad especifica si el control hospedado se puede mostrar su propio menú contextual.

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>Parámetros

*pbAllowContextMenu*<br/>
[out] La dirección de una variable que recibirá el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL utiliza VARIANT_TRUE como el valor predeterminado de esta propiedad.

##  <a name="get_allowshowui"></a>  IAxWinAmbientDispatch::get_AllowShowUI

El `AllowShowUI` propiedad especifica si el control hospedado se puede mostrar su propia interfaz de usuario.

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>Parámetros

*pbAllowShowUI*<br/>
[out] La dirección de una variable que recibirá el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL utiliza VARIANT_FALSE como el valor predeterminado de esta propiedad.

##  <a name="get_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::get_AllowWindowlessActivation

El `AllowWindowlessActivation` propiedad especifica si el contenedor permitirá la activación sin ventana.

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>Parámetros

*pbAllowWindowless*<br/>
[out] La dirección de una variable que recibirá el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL utiliza VARIANT_TRUE como el valor predeterminado de esta propiedad.

##  <a name="get_backcolor"></a>  IAxWinAmbientDispatch::get_BackColor

El `BackColor` propiedad especifica el color de fondo de ambiente del contenedor.

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>Parámetros

*pclrBackground*<br/>
[out] La dirección de una variable que recibirá el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa COLOR_BTNFACE o COLOR_WINDOW como el valor predeterminado de esta propiedad (dependiendo de si el elemento primario de la ventana host es un cuadro de diálogo o no).

##  <a name="get_displayasdefault"></a>  IAxWinAmbientDispatch::get_DisplayAsDefault

`DisplayAsDefault` es una propiedad de ambiente que permite un control averiguar si es el control predeterminado.

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>Parámetros

*pbDisplayAsDefault*<br/>
[out] La dirección de una variable que recibirá el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL utiliza VARIANT_FALSE como el valor predeterminado de esta propiedad.

##  <a name="get_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::get_DocHostDoubleClickFlags

El `DocHostDoubleClickFlags` propiedad especifica la operación que se debe llevar a cabo en respuesta a un doble clic.

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parámetros

*pdwDocHostDoubleClickFlags*<br/>
[out] La dirección de una variable que recibirá el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa DOCHOSTUIDBLCLK_DEFAULT como el valor predeterminado de esta propiedad.

##  <a name="get_dochostflags"></a>  IAxWinAmbientDispatch::get_DocHostFlags

El `DocHostFlags` propiedad especifica las capacidades de la interfaz de usuario del objeto host.

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>Parámetros

*pdwDocHostFlags*<br/>
[out] La dirección de una variable que recibirá el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa DOCHOSTUIFLAG_NO3DBORDER como el valor predeterminado de esta propiedad.

##  <a name="get_font"></a>  IAxWinAmbientDispatch::get_Font

El `Font` propiedad especifica la fuente de ambiente del contenedor.

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>Parámetros

*pFont*<br/>
[out] La dirección de un `IFontDisp` puntero de interfaz que se utiliza para recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto ATL host usa la fuente predeterminada de la interfaz gráfica de usuario o la fuente del sistema como el valor predeterminado de esta propiedad.

##  <a name="get_forecolor"></a>  IAxWinAmbientDispatch::get_ForeColor

El `ForeColor` propiedad especifica el color de primer plano ambiente del contenedor.

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>Parámetros

*pclrForeground*<br/>
[out] La dirección de una variable que recibirá el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa el color de texto de la ventana de sistema como el valor predeterminado de esta propiedad.

##  <a name="get_localeid"></a>  IAxWinAmbientDispatch::get_LocaleID

El `LocaleID` propiedad especifica el identificador de configuración regional de ambiente del contenedor.

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>Parámetros

*plcidLocaleID*<br/>
[out] La dirección de una variable que recibirá el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto ATL host usa la configuración regional predeterminada del usuario como el valor predeterminado de esta propiedad.

Con este método puede detectar el valor de LocalID ambiente, es decir, el LocaleID del programa se utiliza el control está en. Una vez que sepa el LocaleID, puede llamar a código para cargar títulos específicos de la configuración regional, el texto de mensaje de error, y así sucesivamente desde un archivo de recursos o un archivo DLL satélite.

##  <a name="get_messagereflect"></a>  IAxWinAmbientDispatch::get_MessageReflect

El `MessageReflect` propiedad ambiente especifica si el contenedor reflejará los mensajes para el control hospedado.

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>Parámetros

*pbMessageReflect*<br/>
[out] La dirección de una variable que recibirá el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL utiliza VARIANT_TRUE como el valor predeterminado de esta propiedad.

##  <a name="get_optionkeypath"></a>  IAxWinAmbientDispatch::get_OptionKeyPath

El `OptionKeyPath` propiedad especifica la ruta de acceso de clave del registro a la configuración de usuario.

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>Parámetros

*pbstrOptionKeyPath*<br/>
[out] La dirección de una variable que recibirá el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="get_showgrabhandles"></a>  IAxWinAmbientDispatch::get_ShowGrabHandles

El `ShowGrabHandles` propiedad ambiente permite que el control averiguar si debe dibujar con controladores de arrastre.

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>Parámetros

*pbShowGrabHandles*<br/>
[out] La dirección de una variable que recibirá el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación de objeto de host ATL siempre devuelve VARIANT_FALSE como el valor de esta propiedad.

##  <a name="get_showhatching"></a>  IAxWinAmbientDispatch::get_ShowHatching

El `ShowHatching` propiedad ambiente permite que el control averiguar si debe dibujarse a sí mismo sombreada.

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>Parámetros

*pbShowHatching*<br/>
[out] La dirección de una variable que recibirá el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación de objeto de host ATL siempre devuelve VARIANT_FALSE como el valor de esta propiedad.

##  <a name="get_usermode"></a>  IAxWinAmbientDispatch::get_UserMode

El `UserMode` propiedad especifica el modo de usuario de ambiente del contenedor.

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>Parámetros

*pbUserMode*<br/>
[out] La dirección de una variable que recibirá el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL utiliza VARIANT_TRUE como el valor predeterminado de esta propiedad.

##  <a name="put_allowcontextmenu"></a>  IAxWinAmbientDispatch::put_AllowContextMenu

El `AllowContextMenu` propiedad especifica si el control hospedado se puede mostrar su propio menú contextual.

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>Parámetros

*bAllowContextMenu*<br/>
[in] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL utiliza VARIANT_TRUE como el valor predeterminado de esta propiedad.

##  <a name="put_allowshowui"></a>  IAxWinAmbientDispatch::put_AllowShowUI

El `AllowShowUI` propiedad especifica si el control hospedado se puede mostrar su propia interfaz de usuario.

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>Parámetros

*bAllowShowUI*<br/>
[in] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL utiliza VARIANT_FALSE como el valor predeterminado de esta propiedad.

##  <a name="put_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::put_AllowWindowlessActivation

El `AllowWindowlessActivation` propiedad especifica si el contenedor permitirá la activación sin ventana.

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>Parámetros

*bAllowWindowless*<br/>
[in] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL utiliza VARIANT_TRUE como el valor predeterminado de esta propiedad.

##  <a name="put_backcolor"></a>  IAxWinAmbientDispatch::put_BackColor

El `BackColor` propiedad especifica el color de fondo de ambiente del contenedor.

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>Parámetros

*clrBackground*<br/>
[in] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa COLOR_BTNFACE o COLOR_WINDOW como el valor predeterminado de esta propiedad (dependiendo de si el elemento primario de la ventana host es un cuadro de diálogo o no).

##  <a name="put_displayasdefault"></a>  IAxWinAmbientDispatch::put_DisplayAsDefault

`DisplayAsDefault` es una propiedad de ambiente que permite un control averiguar si es el control predeterminado.

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>Parámetros

*bDisplayAsDefault*<br/>
[in] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL utiliza VARIANT_FALSE como el valor predeterminado de esta propiedad.

##  <a name="put_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::put_DocHostDoubleClickFlags

El `DocHostDoubleClickFlags` propiedad especifica la operación que se debe llevar a cabo en respuesta a un doble clic.

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parámetros

*dwDocHostDoubleClickFlags*<br/>
[in] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa DOCHOSTUIDBLCLK_DEFAULT como el valor predeterminado de esta propiedad.

##  <a name="put_dochostflags"></a>  IAxWinAmbientDispatch::put_DocHostFlags

El `DocHostFlags` propiedad especifica las capacidades de la interfaz de usuario del objeto host.

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>Parámetros

*dwDocHostFlags*<br/>
[in] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa DOCHOSTUIFLAG_NO3DBORDER como el valor predeterminado de esta propiedad.

##  <a name="put_font"></a>  IAxWinAmbientDispatch::put_Font

El `Font` propiedad especifica la fuente de ambiente del contenedor.

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>Parámetros

*pFont*<br/>
[in] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto ATL host usa la fuente predeterminada de la interfaz gráfica de usuario o la fuente del sistema como el valor predeterminado de esta propiedad.

##  <a name="put_forecolor"></a>  IAxWinAmbientDispatch::put_ForeColor

El `ForeColor` propiedad especifica el color de primer plano ambiente del contenedor.

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>Parámetros

*clrForeground*<br/>
[in] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa el color de texto de la ventana de sistema como el valor predeterminado de esta propiedad.

##  <a name="put_localeid"></a>  IAxWinAmbientDispatch::put_LocaleID

El `LocaleID` propiedad especifica el identificador de configuración regional de ambiente del contenedor.

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>Parámetros

*lcidLocaleID*<br/>
[in] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto ATL host usa la configuración regional predeterminada del usuario como el valor predeterminado de esta propiedad.

##  <a name="put_messagereflect"></a>  IAxWinAmbientDispatch::put_MessageReflect

El `MessageReflect` propiedad ambiente especifica si el contenedor reflejará los mensajes para el control hospedado.

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>Parámetros

*bMessageReflect*<br/>
[in] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL utiliza VARIANT_TRUE como el valor predeterminado de esta propiedad.

##  <a name="put_optionkeypath"></a>  IAxWinAmbientDispatch::put_OptionKeyPath

El `OptionKeyPath` propiedad especifica la ruta de acceso de clave del registro a la configuración de usuario.

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>Parámetros

*bstrOptionKeyPath*<br/>
[in] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="put_usermode"></a>  IAxWinAmbientDispatch::put_UserMode

El `UserMode` propiedad especifica el modo de usuario de ambiente del contenedor.

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>Parámetros

*bUserMode*<br/>
[in] El nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL utiliza VARIANT_TRUE como el valor predeterminado de esta propiedad.

## <a name="see-also"></a>Vea también

[IAxWinAmbientDispatchEx (interfaz)](../../atl/reference/iaxwinambientdispatchex-interface.md)<br/>
[IAxWinHostWindow (interfaz)](../../atl/reference/iaxwinhostwindow-interface.md)<br/>
[CAxWindow:: QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)

