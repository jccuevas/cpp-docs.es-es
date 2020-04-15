---
title: Clase IAtlMemMgr
ms.date: 11/04/2016
f1_keywords:
- IAtlMemMgr
- ATLMEM/ATL::IAtlMemMgr
- ATLMEM/ATL::Allocate
- ATLMEM/ATL::Free
- ATLMEM/ATL::GetSize
- ATLMEM/ATL::Reallocate
helpviewer_keywords:
- IAtlMemMgr class
- memory, managing
- memory, memory manager
ms.assetid: 18b2c569-25fe-4464-bdb6-3b1abef7154a
ms.openlocfilehash: c296c9de79c305d0f7d2f135f250d181d3cd667a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330065"
---
# <a name="iatlmemmgr-class"></a>Clase IAtlMemMgr

Esta clase representa la interfaz de un administrador de memoria.

## <a name="syntax"></a>Sintaxis

```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[Asignar](#allocate)|Llame a este método para asignar un bloque de memoria.|
|[Gratuito](#free)|Llame a este método para liberar un bloque de memoria.|
|[GetSize](#getsize)|Llame a este método para recuperar el tamaño de un bloque de memoria asignado.|
|[Reasignar](#reallocate)|Llame a este método para reasignar un bloque de memoria.|

## <a name="remarks"></a>Observaciones

Esta interfaz se implementa mediante [CComHeap](../../atl/reference/ccomheap-class.md), [CCRTHeap](../../atl/reference/ccrtheap-class.md), [CLocalHeap](../../atl/reference/clocalheap-class.md), [CGlobalHeap](../../atl/reference/cglobalheap-class.md)o [CWin32Heap](../../atl/reference/cwin32heap-class.md).

> [!NOTE]
> Las funciones de montón local y global son más lentas que otras funciones de administración de memoria y no proporcionan tantas características. Por lo tanto, las nuevas aplicaciones deben utilizar las [funciones de montón.](/windows/win32/Memory/heap-functions) Están disponibles en la clase [CWin32Heap.](../../atl/reference/cwin32heap-class.md)

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** atlmem.h

## <a name="iatlmemmgrallocate"></a><a name="allocate"></a>IAtlMemMgr::Asignar

Llame a este método para asignar un bloque de memoria.

```
void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*nBytes*<br/>
Número de bytes solicitado en el nuevo bloque de memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al principio del bloque de memoria recién asignado.

### <a name="remarks"></a>Observaciones

Llame a [IAtlMemMgr::Free](#free) o [IAtlMemMgr::Reallocate](#reallocate) para liberar la memoria asignada por este método.

### <a name="example"></a>Ejemplo

Para obtener un ejemplo, vea información general de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrfree"></a><a name="free"></a>IAtlMemMgr::Gratis

Llame a este método para liberar un bloque de memoria.

```
void Free(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria.

### <a name="remarks"></a>Observaciones

Utilice este método para liberar memoria obtenida por [IAtlMemMgr::Allocate](#allocate) o [IAtlMemMgr::Reallocate](#reallocate).

### <a name="example"></a>Ejemplo

Para obtener un ejemplo, vea información general de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrgetsize"></a><a name="getsize"></a>IAtlMemMgr::GetSize

Llame a este método para recuperar el tamaño de un bloque de memoria asignado.

```
size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve el tamaño del bloque de memoria en bytes.

### <a name="example"></a>Ejemplo

Para obtener un ejemplo, vea información general de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrreallocate"></a><a name="reallocate"></a>IAtlMemMgr::Reallocate

Llame a este método para reasignar la memoria asignada por este administrador de memoria.

```
void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria.

*nBytes*<br/>
Número de bytes solicitado en el nuevo bloque de memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al principio del bloque de memoria recién asignado.

### <a name="remarks"></a>Observaciones

Llame a [IAtlMemMgr::Free](#free) o [IAtlMemMgr::Reallocate](#reallocate) para liberar la memoria asignada por este método.

Conceptualmente, este método libera la memoria existente y asigna un nuevo bloque de memoria. En realidad, la memoria existente puede extenderse o reutilizarse de otro modo.

### <a name="example"></a>Ejemplo

Para obtener un ejemplo, vea información general de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

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

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a>IAxWinAmbientDispatchEx::SetAmbientDispatch

Se llama a este método para complementar la interfaz de propiedad ambiental predeterminada con una interfaz definida por el usuario.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Parámetros

*pDispatch*<br/>
Puntero a la nueva interfaz.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Cuando `SetAmbientDispatch` se llama con un puntero a una nueva interfaz, esta nueva interfaz se usará para invocar las propiedades o métodos solicitados por el control hospedado, si [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)no proporciona ya esas propiedades.

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a>IAxWinHostWindow::AttachControl

Asocia un control existente (y inicializado previamente) al objeto host mediante la ventana identificada por *hWnd*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*pUnkControl*<br/>
[en] Puntero a `IUnknown` la interfaz del control que se va a adjuntar al objeto host.

*hWnd*<br/>
[en] Identificador de la ventana que se usará para hospedar.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a>IAxWinHostWindow::CreateControl

Crea un control, lo inicializa y lo hospeda en la ventana identificada por *hWnd*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Parámetros

*lpTricsData*<br/>
[en] Cadena que identifica el control que se va a crear. Puede ser un CLSID (debe incluir las llaves), ProgID, URL o HTML sin formato (prefijado por **MSHTML:**).

*hWnd*<br/>
[en] Identificador de la ventana que se usará para hospedar.

*pStream*<br/>
[en] Puntero de interfaz para una secuencia que contiene datos de inicialización para el control. Puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Esta ventana será subclase por el objeto host que expone esta interfaz para que los mensajes se pueden reflejar en el control y otras características de contenedor funcionarán.

Llamar a este método equivale a llamar a [IAxWinHostWindow::CreateControlEx](#createcontrolex).

Para crear un control ActiveX con licencia, vea [IAxWinHostWindowLic::CreateControlLic](#createcontrollicex).

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a>IAxWinHostWindow::CreateControlEx

Crea un control ActiveX, lo inicializa y lo hospeda en la ventana especificada, similar a [IAxWinHostWindow::CreateControl](#createcontrol).

```
STDMETHOD(CreateControlEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise);
```

### <a name="parameters"></a>Parámetros

*lpTricsData*<br/>
[en] Cadena que identifica el control que se va a crear. Puede ser un CLSID (debe incluir las llaves), ProgID, URL o HTML sin formato (prefijado con **MSHTML:**).

*hWnd*<br/>
[en] Identificador de la ventana que se usará para hospedar.

*pStream*<br/>
[en] Puntero de interfaz para una secuencia que contiene datos de inicialización para el control. Puede ser NULL.

*ppUnk*<br/>
[fuera] La dirección de un puntero `IUnknown` que recibirá la interfaz del control creado. Puede ser NULL.

*riidAdvise*<br/>
[en] Identificador de interfaz de una interfaz saliente en el objeto contenido. Puede ser IID_NULL.

*punkAdvise*<br/>
[en] Puntero a `IUnknown` la interfaz del objeto receptor que se va a conectar `iidSink`al punto de conexión en el objeto contenido especificado por .

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

A `CreateControl` diferencia `CreateControlEx` del método, también permite recibir un puntero de interfaz al control recién creado y configurar un receptor de eventos para recibir eventos desencadenados por el control.

Para crear un control ActiveX con licencia, vea [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex).

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a>IAxWinHostWindow::QueryControl

Devuelve el puntero de interfaz especificado proporcionado por el control hospedado.

```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
[en] El identificador de una interfaz en el control que se solicita.

*ppvObject*<br/>
[fuera] La dirección de un puntero que recibirá la interfaz especificada del control creado.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>IAxWinHostWindow::SetExternalDispatch

Establece el dispinterface externo, que está disponible para los controles contenidos a través de la [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) método.

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Parámetros

*pDisp*<br/>
[en] Un puntero `IDispatch` a una interfaz.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>IAxWinHostWindow::SetExternalUIHandler

Llame a esta función para establecer la interfaz [externa IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) para el `CAxWindow` objeto.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Parámetros

*pDisp*<br/>
[en] Un puntero `IDocHostUIHandlerDispatch` a una interfaz.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Esta función la usan los controles (como el control del explorador `IDocHostUIHandlerDispatch` web) que consultan el sitio del host para la interfaz.

## <a name="iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a>IAxWinHostWindowLic::CreateControlLic

Crea un control con licencia, lo inicializa y `hWnd`lo hospeda en la ventana identificada por .

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parámetros

*bstrLic*<br/>
[en] El BSTR que contiene la clave de licencia para el control.

### <a name="remarks"></a>Observaciones

Vea [IAxWinHostWindow::CreateControl](#createcontrol) para obtener una descripción de los parámetros restantes y el valor devuelto.

Llamar a este método equivale a llamar a [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Ejemplo

Consulte [Hosting ActiveX Controls Using ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `IAxWinHostWindowLic::CreateControlLic`.

## <a name="iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a>IAxWinHostWindowLic::CreateControlLicEx

Crea un control ActiveX con licencia, lo inicializa y lo hospeda en la ventana especificada, similar a [IAxWinHostWindow::CreateControl](#createcontrol).

```
STDMETHOD(CreateControlLicEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parámetros

*bstrLic*<br/>
[en] El BSTR que contiene la clave de licencia para el control.

### <a name="remarks"></a>Observaciones

Vea [IAxWinHostWindow::CreateControlEx](#createcontrolex) para obtener una descripción de los parámetros restantes y el valor devuelto.

### <a name="example"></a>Ejemplo

Consulte [Hosting ActiveX Controls Using ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `IAxWinHostWindowLic::CreateControlLicEx`.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
