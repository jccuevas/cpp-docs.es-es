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
ms.openlocfilehash: a0d79ae95a0604ca75f03673873e99394a1bc295
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496067"
---
# <a name="iatlmemmgr-class"></a>Clase IAtlMemMgr

Esta clase representa la interfaz para un administrador de memoria.

## <a name="syntax"></a>Sintaxis

```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[Allocate](#allocate)|Llame a este método para asignar un bloque de memoria.|
|[Gratis](#free)|Llame a este método para liberar un bloque de memoria.|
|[GetSize](#getsize)|Llame a este método para recuperar el tamaño de un bloque de memoria asignado.|
|[Reallocate](#reallocate)|Llame a este método para reasignar un bloque de memoria.|

## <a name="remarks"></a>Comentarios

Esta interfaz se implementa mediante [CComHeap](../../atl/reference/ccomheap-class.md), [CCRTHeap](../../atl/reference/ccrtheap-class.md), [CLocalHeap](../../atl/reference/clocalheap-class.md), [CGlobalHeap](../../atl/reference/cglobalheap-class.md)o [CWin32Heap](../../atl/reference/cwin32heap-class.md).

> [!NOTE]
>  Las funciones del montón local y global son más lentas que otras funciones de administración de memoria y no proporcionan tantas características. Por lo tanto, las aplicaciones nuevas deben usar las [funciones del montón](/windows/win32/Memory/heap-functions). Están disponibles en la clase [CWin32Heap](../../atl/reference/cwin32heap-class.md) .

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** atlmem. h

##  <a name="allocate"></a>  IAtlMemMgr::Allocate

Llame a este método para asignar un bloque de memoria.

```
void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*nBytes*<br/>
Número de bytes solicitado en el nuevo bloque de memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al principio del bloque de memoria recién asignado.

### <a name="remarks"></a>Comentarios

Llame a [IAtlMemMgr:: Free](#free) o [IAtlMemMgr::](#reallocate) allocate para liberar la memoria asignada por este método.

### <a name="example"></a>Ejemplo

Para obtener un ejemplo, consulte la [información general de IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

##  <a name="free"></a>  IAtlMemMgr::Free

Llame a este método para liberar un bloque de memoria.

```
void Free(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria.

### <a name="remarks"></a>Comentarios

Use este método para liberar la memoria obtenida por [IAtlMemMgr::](#allocate) allocate o [IAtlMemMgr::](#reallocate)allocate.

### <a name="example"></a>Ejemplo

Para obtener un ejemplo, consulte la [información general de IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

##  <a name="getsize"></a>  IAtlMemMgr::GetSize

Llame a este método para recuperar el tamaño de un bloque de memoria asignado.

```
size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve el tamaño del bloque de memoria en bytes.

### <a name="example"></a>Ejemplo

Para obtener un ejemplo, consulte la [información general de IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

##  <a name="reallocate"></a>  IAtlMemMgr::Reallocate

Llame a este método para reasignar la memoria asignada por este administrador de memoria.

```
void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria.

*nBytes*<br/>
Número de bytes solicitado en el nuevo bloque de memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al principio del bloque de memoria recién asignado.

### <a name="remarks"></a>Comentarios

Llame a [IAtlMemMgr:: Free](#free) o [IAtlMemMgr::](#reallocate) allocate para liberar la memoria asignada por este método.

Conceptualmente, este método libera la memoria existente y asigna un nuevo bloque de memoria. En realidad, la memoria existente puede extenderse o reutilizarse de otro modo.

### <a name="example"></a>Ejemplo

Para obtener un ejemplo, consulte la [información general de IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

##  <a name="get_allowcontextmenu"></a>  IAxWinAmbientDispatch::get_AllowContextMenu

La `AllowContextMenu` propiedad especifica si el control hospedado puede mostrar su propio menú contextual.

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>Parámetros

*pbAllowContextMenu*<br/>
enuncia Dirección de una variable que va a recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa VARIANT_TRUE como valor predeterminado de esta propiedad.

##  <a name="get_allowshowui"></a>  IAxWinAmbientDispatch::get_AllowShowUI

La `AllowShowUI` propiedad especifica si el control hospedado puede mostrar su propia interfaz de usuario.

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>Parámetros

*pbAllowShowUI*<br/>
enuncia Dirección de una variable que va a recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa VARIANT_FALSE como valor predeterminado de esta propiedad.

##  <a name="get_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::get_AllowWindowlessActivation

La `AllowWindowlessActivation` propiedad especifica si el contenedor permitirá la activación sin ventanas.

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>Parámetros

*pbAllowWindowless*<br/>
enuncia Dirección de una variable que va a recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa VARIANT_TRUE como valor predeterminado de esta propiedad.

##  <a name="get_backcolor"></a>  IAxWinAmbientDispatch::get_BackColor

La `BackColor` propiedad especifica el color de fondo ambiente del contenedor.

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>Parámetros

*pclrBackground*<br/>
enuncia Dirección de una variable que va a recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL utiliza COLOR_BTNFACE o COLOR_WINDOW como valor predeterminado de esta propiedad (dependiendo de si el elemento primario de la ventana host es un cuadro de diálogo o no).

##  <a name="get_displayasdefault"></a>  IAxWinAmbientDispatch::get_DisplayAsDefault

`DisplayAsDefault`es una propiedad de ambiente que permite a un control averiguar si es el control predeterminado.

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>Parámetros

*pbDisplayAsDefault*<br/>
enuncia Dirección de una variable que va a recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa VARIANT_FALSE como valor predeterminado de esta propiedad.

##  <a name="get_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::get_DocHostDoubleClickFlags

La `DocHostDoubleClickFlags` propiedad especifica la operación que debe tener lugar en respuesta a un doble clic.

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parámetros

*pdwDocHostDoubleClickFlags*<br/>
enuncia Dirección de una variable que va a recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa DOCHOSTUIDBLCLK_DEFAULT como valor predeterminado de esta propiedad.

##  <a name="get_dochostflags"></a>  IAxWinAmbientDispatch::get_DocHostFlags

La `DocHostFlags` propiedad especifica las capacidades de la interfaz de usuario del objeto host.

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>Parámetros

*pdwDocHostFlags*<br/>
enuncia Dirección de una variable que va a recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa DOCHOSTUIFLAG_NO3DBORDER como valor predeterminado de esta propiedad.

##  <a name="get_font"></a>  IAxWinAmbientDispatch::get_Font

La `Font` propiedad especifica la fuente ambiente del contenedor.

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>Parámetros

*pFont*<br/>
enuncia Dirección de un `IFontDisp` puntero de interfaz que se utiliza para recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL utiliza la fuente de GUI predeterminada o la fuente del sistema como valor predeterminado de esta propiedad.

##  <a name="get_forecolor"></a>  IAxWinAmbientDispatch::get_ForeColor

La `ForeColor` propiedad especifica el color de primer plano ambiente del contenedor.

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>Parámetros

*pclrForeground*<br/>
enuncia Dirección de una variable que va a recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa el color del texto de la ventana del sistema como valor predeterminado de esta propiedad.

##  <a name="get_localeid"></a>  IAxWinAmbientDispatch::get_LocaleID

La `LocaleID` propiedad especifica el identificador de configuración regional ambiente del contenedor.

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>Parámetros

*plcidLocaleID*<br/>
enuncia Dirección de una variable que va a recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa la configuración regional predeterminada del usuario como valor predeterminado de esta propiedad.

Con este método puede detectar el LocalID ambiente, es decir, el LocaleID del programa en el que se usa el control. Una vez que conozca el LocaleID, puede llamar a código para cargar los títulos específicos de la configuración regional, el texto del mensaje de error, etc., de un archivo de recursos o un archivo DLL satélite.

##  <a name="get_messagereflect"></a>  IAxWinAmbientDispatch::get_MessageReflect

La `MessageReflect` propiedad ambiente especifica si el contenedor reflejará los mensajes en el control hospedado.

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>Parámetros

*pbMessageReflect*<br/>
enuncia Dirección de una variable que va a recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa VARIANT_TRUE como valor predeterminado de esta propiedad.

##  <a name="get_optionkeypath"></a>  IAxWinAmbientDispatch::get_OptionKeyPath

La `OptionKeyPath` propiedad especifica la ruta de acceso de la clave del registro a la configuración del usuario.

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>Parámetros

*pbstrOptionKeyPath*<br/>
enuncia Dirección de una variable que va a recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="get_showgrabhandles"></a>  IAxWinAmbientDispatch::get_ShowGrabHandles

La `ShowGrabHandles` propiedad ambiente permite al control averiguar si debe dibujarse con los controladores de arrastre.

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>Parámetros

*pbShowGrabHandles*<br/>
enuncia Dirección de una variable que va a recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL siempre devuelve VARIANT_FALSE como el valor de esta propiedad.

##  <a name="get_showhatching"></a>  IAxWinAmbientDispatch::get_ShowHatching

La `ShowHatching` propiedad ambiente permite al control averiguar si debe dibujarse a sí mismo sombreado.

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>Parámetros

*pbShowHatching*<br/>
enuncia Dirección de una variable que va a recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL siempre devuelve VARIANT_FALSE como el valor de esta propiedad.

##  <a name="get_usermode"></a>  IAxWinAmbientDispatch::get_UserMode

La `UserMode` propiedad especifica el modo de usuario ambiente del contenedor.

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>Parámetros

*pbUserMode*<br/>
enuncia Dirección de una variable que va a recibir el valor actual de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa VARIANT_TRUE como valor predeterminado de esta propiedad.

##  <a name="put_allowcontextmenu"></a>  IAxWinAmbientDispatch::put_AllowContextMenu

La `AllowContextMenu` propiedad especifica si el control hospedado puede mostrar su propio menú contextual.

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>Parámetros

*bAllowContextMenu*<br/>
de Nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa VARIANT_TRUE como valor predeterminado de esta propiedad.

##  <a name="put_allowshowui"></a>  IAxWinAmbientDispatch::put_AllowShowUI

La `AllowShowUI` propiedad especifica si el control hospedado puede mostrar su propia interfaz de usuario.

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>Parámetros

*bAllowShowUI*<br/>
de Nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa VARIANT_FALSE como valor predeterminado de esta propiedad.

##  <a name="put_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::put_AllowWindowlessActivation

La `AllowWindowlessActivation` propiedad especifica si el contenedor permitirá la activación sin ventanas.

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>Parámetros

*bAllowWindowless*<br/>
de Nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa VARIANT_TRUE como valor predeterminado de esta propiedad.

##  <a name="put_backcolor"></a>  IAxWinAmbientDispatch::put_BackColor

La `BackColor` propiedad especifica el color de fondo ambiente del contenedor.

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>Parámetros

*clrBackground*<br/>
de Nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL utiliza COLOR_BTNFACE o COLOR_WINDOW como valor predeterminado de esta propiedad (dependiendo de si el elemento primario de la ventana host es un cuadro de diálogo o no).

##  <a name="put_displayasdefault"></a>  IAxWinAmbientDispatch::put_DisplayAsDefault

`DisplayAsDefault`es una propiedad de ambiente que permite a un control averiguar si es el control predeterminado.

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>Parámetros

*bDisplayAsDefault*<br/>
de Nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa VARIANT_FALSE como valor predeterminado de esta propiedad.

##  <a name="put_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::put_DocHostDoubleClickFlags

La `DocHostDoubleClickFlags` propiedad especifica la operación que debe tener lugar en respuesta a un doble clic.

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parámetros

*dwDocHostDoubleClickFlags*<br/>
de Nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa DOCHOSTUIDBLCLK_DEFAULT como valor predeterminado de esta propiedad.

##  <a name="put_dochostflags"></a>  IAxWinAmbientDispatch::put_DocHostFlags

La `DocHostFlags` propiedad especifica las capacidades de la interfaz de usuario del objeto host.

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>Parámetros

*dwDocHostFlags*<br/>
de Nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa DOCHOSTUIFLAG_NO3DBORDER como valor predeterminado de esta propiedad.

##  <a name="put_font"></a>  IAxWinAmbientDispatch::put_Font

La `Font` propiedad especifica la fuente ambiente del contenedor.

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>Parámetros

*pFont*<br/>
de Nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL utiliza la fuente de GUI predeterminada o la fuente del sistema como valor predeterminado de esta propiedad.

##  <a name="put_forecolor"></a>  IAxWinAmbientDispatch::put_ForeColor

La `ForeColor` propiedad especifica el color de primer plano ambiente del contenedor.

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>Parámetros

*clrForeground*<br/>
de Nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa el color del texto de la ventana del sistema como valor predeterminado de esta propiedad.

##  <a name="put_localeid"></a>  IAxWinAmbientDispatch::put_LocaleID

La `LocaleID` propiedad especifica el identificador de configuración regional ambiente del contenedor.

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>Parámetros

*lcidLocaleID*<br/>
de Nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa la configuración regional predeterminada del usuario como valor predeterminado de esta propiedad.

##  <a name="put_messagereflect"></a>  IAxWinAmbientDispatch::put_MessageReflect

La `MessageReflect` propiedad ambiente especifica si el contenedor reflejará los mensajes en el control hospedado.

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>Parámetros

*bMessageReflect*<br/>
de Nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa VARIANT_TRUE como valor predeterminado de esta propiedad.

##  <a name="put_optionkeypath"></a>  IAxWinAmbientDispatch::put_OptionKeyPath

La `OptionKeyPath` propiedad especifica la ruta de acceso de la clave del registro a la configuración del usuario.

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>Parámetros

*bstrOptionKeyPath*<br/>
de Nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="put_usermode"></a>  IAxWinAmbientDispatch::put_UserMode

La `UserMode` propiedad especifica el modo de usuario ambiente del contenedor.

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>Parámetros

*bUserMode*<br/>
de Nuevo valor de esta propiedad.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación del objeto host ATL usa VARIANT_TRUE como valor predeterminado de esta propiedad.

##  <a name="setambientdispatch"></a>  IAxWinAmbientDispatchEx::SetAmbientDispatch

Se llama a este método para complementar la interfaz de propiedades ambiente predeterminada con una interfaz definida por el usuario.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Parámetros

*pDispatch*<br/>
Puntero a la nueva interfaz.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Cuando `SetAmbientDispatch` se llama a con un puntero a una nueva interfaz, esta nueva interfaz se usará para invocar cualquier propiedad o método que el control hospedado solicite, si las propiedades no están ya proporcionadas por [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).

##  <a name="attachcontrol"></a>  IAxWinHostWindow::AttachControl

Asocia un control existente (y previamente inicializado) al objeto host mediante la ventana identificada por *hWnd*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*pUnkControl*<br/>
de Puntero a la `IUnknown` interfaz del control que se va a adjuntar al objeto host.

*hWnd*<br/>
de Identificador de la ventana que se va a usar para hospedar.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="createcontrol"></a>  IAxWinHostWindow::CreateControl

Crea un control, lo inicializa y lo hospeda en la ventana identificada por *hWnd*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Parámetros

*lpTricsData*<br/>
de Cadena que identifica el control que se va a crear. Puede ser un CLSID (debe incluir las llaves), ProgID, URL o HTML sin formato (con el prefijo **MSHTML:** ).

*hWnd*<br/>
de Identificador de la ventana que se va a usar para hospedar.

*pStream*<br/>
de Puntero de interfaz para una secuencia que contiene los datos de inicialización del control. Puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

El objeto host que expone esta interfaz creará una subclase de esta ventana para que los mensajes se puedan reflejar en el control y otras características del contenedor funcionen.

Llamar a este método equivale a llamar a [IAxWinHostWindow:: CreateControlEx](#createcontrolex).

Para crear un control ActiveX con licencia, vea [IAxWinHostWindowLic:: CreateControlLic](#createcontrollicex).

##  <a name="createcontrolex"></a>  IAxWinHostWindow::CreateControlEx

Crea un control ActiveX, lo inicializa y lo hospeda en la ventana especificada, de forma similar a [IAxWinHostWindow:: CreateControl](#createcontrol).

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
de Cadena que identifica el control que se va a crear. Puede ser un CLSID (debe incluir las llaves), ProgID, URL o HTML sin formato (con **MSHTML:** ) como prefijo.

*hWnd*<br/>
de Identificador de la ventana que se va a usar para hospedar.

*pStream*<br/>
de Puntero de interfaz para una secuencia que contiene los datos de inicialización del control. Puede ser NULL.

*ppUnk*<br/>
enuncia La dirección de un puntero que recibirá la `IUnknown` interfaz del control creado. Puede ser NULL.

*riidAdvise*<br/>
de Identificador de interfaz de una interfaz de salida en el objeto contenido. Puede ser IID_NULL.

*punkAdvise*<br/>
de Puntero a la `IUnknown` interfaz del objeto receptor que se va a conectar al punto de conexión en el objeto contenido especificado por `iidSink`.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

A diferencia del `CreateControl` método, `CreateControlEx` también permite recibir un puntero de interfaz al control recién creado y configurar un receptor de eventos para recibir los eventos desencadenados por el control.

Para crear un control ActiveX con licencia, vea [IAxWinHostWindowLic:: CreateControlLicEx](#createcontrollicex).

##  <a name="querycontrol"></a>  IAxWinHostWindow::QueryControl

Devuelve el puntero de interfaz especificado proporcionado por el control hospedado.

```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
de IDENTIFICADOR de una interfaz en el control que se va a solicitar.

*ppvObject*<br/>
enuncia Dirección de un puntero que recibirá la interfaz especificada del control creado.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="setexternaldispatch"></a>  IAxWinHostWindow::SetExternalDispatch

Establece la dispinterface externa, que está disponible para los controles contenidos a través del método [IDocHostUIHandlerDispatch:: GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) .

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Parámetros

*pDisp*<br/>
de Puntero a una `IDispatch` interfaz.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="setexternaluihandler"></a>  IAxWinHostWindow::SetExternalUIHandler

Llame a esta función para establecer la interfaz [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) externa para `CAxWindow` el objeto.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Parámetros

*pDisp*<br/>
de Puntero a una `IDocHostUIHandlerDispatch` interfaz.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Esta función la usan los controles (como el control de explorador Web) que consultan la `IDocHostUIHandlerDispatch` interfaz en el sitio del host.

##  <a name="createcontrollic"></a>  IAxWinHostWindowLic::CreateControlLic

Crea un control con licencia, lo inicializa y lo hospeda en la ventana identificada por `hWnd`.

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parámetros

*bstrLic*<br/>
de BSTR que contiene la clave de licencia para el control.

### <a name="remarks"></a>Comentarios

Vea [IAxWinHostWindow:: CreateControl](#createcontrol) para obtener una descripción de los parámetros restantes y el valor devuelto.

Llamar a este método equivale a llamar a [IAxWinHostWindowLic:: CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Ejemplo

Vea [hospedar controles ActiveX mediante la AxHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener `IAxWinHostWindowLic::CreateControlLic`un ejemplo que usa.

##  <a name="createcontrollicex"></a>  IAxWinHostWindowLic::CreateControlLicEx

Crea un control ActiveX con licencia, lo inicializa y lo hospeda en la ventana especificada, de forma similar a [IAxWinHostWindow:: CreateControl](#createcontrol).

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
de BSTR que contiene la clave de licencia para el control.

### <a name="remarks"></a>Comentarios

Vea [IAxWinHostWindow:: CreateControlEx](#createcontrolex) para obtener una descripción de los parámetros restantes y el valor devuelto.

### <a name="example"></a>Ejemplo

Vea [hospedar controles ActiveX mediante la AxHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener `IAxWinHostWindowLic::CreateControlLicEx`un ejemplo que usa.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
