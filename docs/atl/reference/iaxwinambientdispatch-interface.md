---
title: Interfaz IAxWinAmbientDispatch | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinAmbientDispatch
- No header/ATL::IAxWinAmbientDispatch
- No header/ATL::get_AllowContextMenu
- No header/ATL::get_AllowShowUI
- No header/ATL::get_AllowWindowlessActivation
- No header/ATL::get_BackColor
- No header/ATL::get_DisplayAsDefault
- No header/ATL::get_DocHostDoubleClickFlags
- No header/ATL::get_DocHostFlags
- No header/ATL::get_Font
- No header/ATL::get_ForeColor
- No header/ATL::get_LocaleID
- No header/ATL::get_MessageReflect
- No header/ATL::get_OptionKeyPath
- No header/ATL::get_ShowGrabHandles
- No header/ATL::get_ShowHatching
- No header/ATL::get_UserMode
- No header/ATL::put_AllowContextMenu
- No header/ATL::put_AllowShowUI
- No header/ATL::put_AllowWindowlessActivation
- No header/ATL::put_BackColor
- No header/ATL::put_DisplayAsDefault
- No header/ATL::put_DocHostDoubleClickFlags
- No header/ATL::put_DocHostFlags
- No header/ATL::put_Font
- No header/ATL::put_ForeColor
- No header/ATL::put_LocaleID
- No header/ATL::put_MessageReflect
- No header/ATL::put_OptionKeyPath
- No header/ATL::put_UserMode
dev_langs:
- C++
helpviewer_keywords:
- IAxWinAmbientDispatch interface
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
caps.latest.revision: 24
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
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 3dd34ffec68e4503aebe7b8d0e72ec1f711dca03
ms.contentlocale: es-es
ms.lasthandoff: 03/31/2017

---
# <a name="iaxwinambientdispatch-interface"></a>Interfaz IAxWinAmbientDispatch
Esta interfaz proporciona métodos para especificar las características del control hospedado o contenedor.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```
interface IAxWinAmbientDispatch : IDispatch
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[get_AllowContextMenu](#get_allowcontextmenu)|El **AllowContextMenu** propiedad especifica si el control hospedado tiene permiso para mostrar su propio menú contextual.|  
|[get_AllowShowUI](#get_allowshowui)|El **AllowShowUI** propiedad especifica si el control hospedado tiene permiso para mostrar su propia interfaz de usuario.|  
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|El **AllowWindowlessActivation** propiedad especifica si el contenedor permitirá la activación sin ventana.|  
|[get_BackColor](#get_backcolor)|El `BackColor` propiedad especifica el color de fondo ambiente del contenedor.|  
|[get_DisplayAsDefault](#get_displayasdefault)|**DisplayAsDefault** es una propiedad de ambiente que permite que un control averiguar si es el control predeterminado.|  
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|El **DocHostDoubleClickFlags** propiedad especifica la operación que debe tener lugar en respuesta a un doble clic.|  
|[get_DocHostFlags](#get_dochostflags)|El **DocHostFlags** propiedad especifica las funciones de la interfaz de usuario del objeto host.|  
|[get_Font](#get_font)|El **fuente** propiedad especifica la fuente ambiente del contenedor.|  
|[get_ForeColor](#get_forecolor)|El `ForeColor` propiedad especifica el color de primer plano ambiente del contenedor.|  
|[get_LocaleID](#get_localeid)|El **LocaleID** propiedad especifica el identificador de configuración regional de ambiente del contenedor.|  
|[get_MessageReflect](#get_messagereflect)|El **MessageReflect** propiedad de ambiente especifica si el contenedor reflejarán los mensajes para el control hospedado.|  
|[get_OptionKeyPath](#get_optionkeypath)|El **OptionKeyPath** propiedad especifica la ruta de acceso de clave del registro a la configuración de usuario.|  
|[get_ShowGrabHandles](#get_showgrabhandles)|El **ShowGrabHandles** propiedad de ambiente permite que el control averiguar si debe dibujar con asas de captación.|  
|[get_ShowHatching](#get_showhatching)|El **ShowHatching** propiedad de ambiente permite que el control averiguar si debe dibujar propio sombreada.|  
|[get_UserMode](#get_usermode)|El **UserMode** propiedad especifica el modo de usuario de ambiente del contenedor.|  
|[put_AllowContextMenu](#put_allowcontextmenu)|El **AllowContextMenu** propiedad especifica si el control hospedado tiene permiso para mostrar su propio menú contextual.|  
|[put_AllowShowUI](#put_allowshowui)|El **AllowShowUI** propiedad especifica si el control hospedado tiene permiso para mostrar su propia interfaz de usuario.|  
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|El **AllowWindowlessActivation** propiedad especifica si el contenedor permitirá la activación sin ventana.|  
|[put_BackColor](#put_backcolor)|El `BackColor` propiedad especifica el color de fondo ambiente del contenedor.|  
|[put_DisplayAsDefault](#put_displayasdefault)|**DisplayAsDefault** es una propiedad de ambiente que permite que un control averiguar si es el control predeterminado.|  
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|El **DocHostDoubleClickFlags** propiedad especifica la operación que debe tener lugar en respuesta a un doble clic.|  
|[put_DocHostFlags](#put_dochostflags)|El **DocHostFlags** propiedad especifica las funciones de la interfaz de usuario del objeto host.|  
|[put_Font](#put_font)|El **fuente** propiedad especifica la fuente ambiente del contenedor.|  
|[put_ForeColor](#put_forecolor)|El `ForeColor` propiedad especifica el color de primer plano ambiente del contenedor.|  
|[put_LocaleID](#put_localeid)|El **LocaleID** propiedad especifica el identificador de configuración regional de ambiente del contenedor.|  
|[put_MessageReflect](#put_messagereflect)|El **MessageReflect** propiedad de ambiente especifica si el contenedor reflejarán los mensajes para el control hospedado.|  
|[put_OptionKeyPath](#put_optionkeypath)|El **OptionKeyPath** propiedad especifica la ruta de acceso de clave del registro a la configuración de usuario.|  
|[put_UserMode](#put_usermode)|El **UserMode** propiedad especifica el modo de usuario de ambiente del contenedor.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se expone mediante objetos que hospeda los controles ActiveX de ATL. Llamar a los métodos de esta interfaz para establecer las propiedades de ambiente disponibles en el control hospedado o para especificar otros aspectos del comportamiento del contenedor. Para complementar las propiedades proporcionadas por `IAxWinAmbientDispatch`, use [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md).  
  
 [AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx) intentará cargar la información de tipo sobre `IAxWinAmbientDispatch` y `IAxWinAmbientDispatchEx` desde la biblioteca de tipos que contiene el código.  
  
 Si está vinculando ATL90.dll, **AXHost** cargará la información de tipo de la biblioteca de tipos del archivo DLL.  
  
 Vea [hospedaje de controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener más detalles.  
  
## <a name="requirements"></a>Requisitos  
 La definición de esta interfaz está disponible en varios formatos, como se muestra en la tabla siguiente.  
  
|Tipo de definición|Archivo|  
|---------------------|----------|  
|IDL|atliface.idl|  
|Biblioteca de tipos|ATL.dll|  
|C++|atliface.h (que también se incluye en ATLBase.h)|  
  
##  <a name="get_allowcontextmenu"></a>IAxWinAmbientDispatch::get_AllowContextMenu  
 El **AllowContextMenu** propiedad especifica si el control hospedado tiene permiso para mostrar su propio menú contextual.  
  
```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 *pbAllowContextMenu*  
 [out] La dirección de una variable que recibirá el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa `VARIANT_TRUE` como el valor predeterminado de esta propiedad.  
  
##  <a name="get_allowshowui"></a>IAxWinAmbientDispatch::get_AllowShowUI  
 El **AllowShowUI** propiedad especifica si el control hospedado tiene permiso para mostrar su propia interfaz de usuario.  
  
```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```  
  
### <a name="parameters"></a>Parámetros  
 *pbAllowShowUI*  
 [out] La dirección de una variable que recibirá el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa **VARIANT_FALSE** como el valor predeterminado de esta propiedad.  
  
##  <a name="get_allowwindowlessactivation"></a>IAxWinAmbientDispatch::get_AllowWindowlessActivation  
 El **AllowWindowlessActivation** propiedad especifica si el contenedor permitirá la activación sin ventana.  
  
```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```  
  
### <a name="parameters"></a>Parámetros  
 *pbAllowWindowless*  
 [out] La dirección de una variable que recibirá el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa `VARIANT_TRUE` como el valor predeterminado de esta propiedad.  
  
##  <a name="get_backcolor"></a>IAxWinAmbientDispatch::get_BackColor  
 El `BackColor` propiedad especifica el color de fondo ambiente del contenedor.  
  
```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```  
  
### <a name="parameters"></a>Parámetros  
 *pclrBackground*  
 [out] La dirección de una variable que recibirá el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa **COLOR_BTNFACE** o **COLOR_WINDOW** como el valor predeterminado de esta propiedad (en función de si el elemento primario de la ventana del host es un cuadro de diálogo o no).  
  
##  <a name="get_displayasdefault"></a>IAxWinAmbientDispatch::get_DisplayAsDefault  
 **DisplayAsDefault** es una propiedad de ambiente que permite que un control averiguar si es el control predeterminado.  
  
```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```  
  
### <a name="parameters"></a>Parámetros  
 *pbDisplayAsDefault*  
 [out] La dirección de una variable que recibirá el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa **VARIANT_FALSE** como el valor predeterminado de esta propiedad.  
  
##  <a name="get_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::get_DocHostDoubleClickFlags  
 El **DocHostDoubleClickFlags** propiedad especifica la operación que debe tener lugar en respuesta a un doble clic.  
  
```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 *pdwDocHostDoubleClickFlags*  
 [out] La dirección de una variable que recibirá el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa **DOCHOSTUIDBLCLK_DEFAULT** como el valor predeterminado de esta propiedad.  
  
##  <a name="get_dochostflags"></a>IAxWinAmbientDispatch::get_DocHostFlags  
 El **DocHostFlags** propiedad especifica las funciones de la interfaz de usuario del objeto host.  
  
```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 *pdwDocHostFlags*  
 [out] La dirección de una variable que recibirá el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa **DOCHOSTUIFLAG_NO3DBORDER** como el valor predeterminado de esta propiedad.  
  
##  <a name="get_font"></a>IAxWinAmbientDispatch::get_Font  
 El **fuente** propiedad especifica la fuente ambiente del contenedor.  
  
```
STDMETHOD(get_Font)(IFontDisp** pFont);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFont`  
 [out] La dirección de un **IFontDisp** puntero de interfaz que se utiliza para recibir el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa la fuente de la interfaz gráfica de usuario predeterminada o la fuente del sistema como el valor predeterminado de esta propiedad.  
  
##  <a name="get_forecolor"></a>IAxWinAmbientDispatch::get_ForeColor  
 El `ForeColor` propiedad especifica el color de primer plano ambiente del contenedor.  
  
```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```  
  
### <a name="parameters"></a>Parámetros  
 *pclrForeground*  
 [out] La dirección de una variable que recibirá el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa el color de texto de la ventana de sistema como el valor predeterminado de esta propiedad.  
  
##  <a name="get_localeid"></a>IAxWinAmbientDispatch::get_LocaleID  
 El **LocaleID** propiedad especifica el identificador de configuración regional de ambiente del contenedor.  
  
```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```  
  
### <a name="parameters"></a>Parámetros  
 *plcidLocaleID*  
 [out] La dirección de una variable que recibirá el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa el idioma del usuario predeterminado como el valor predeterminado de esta propiedad.  
  
 Con este método puede detectar el LocalID ambiente, es decir, el valor de LocaleID del programa se utiliza el control está en. Una vez que sepa el identificador de configuración regional, se puede llamar a código para cargar títulos de configuración regional, texto de mensaje de error, y así sucesivamente desde un archivo de recursos o un archivo DLL satélite.  
  
##  <a name="get_messagereflect"></a>IAxWinAmbientDispatch::get_MessageReflect  
 El **MessageReflect** propiedad de ambiente especifica si el contenedor reflejarán los mensajes para el control hospedado.  
  
```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```  
  
### <a name="parameters"></a>Parámetros  
 *pbMessageReflect*  
 [out] La dirección de una variable que recibirá el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa `VARIANT_TRUE` como el valor predeterminado de esta propiedad.  
  
##  <a name="get_optionkeypath"></a>IAxWinAmbientDispatch::get_OptionKeyPath  
 El **OptionKeyPath** propiedad especifica la ruta de acceso de clave del registro a la configuración de usuario.  
  
```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```  
  
### <a name="parameters"></a>Parámetros  
 *pbstrOptionKeyPath*  
 [out] La dirección de una variable que recibirá el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="get_showgrabhandles"></a>IAxWinAmbientDispatch::get_ShowGrabHandles  
 El **ShowGrabHandles** propiedad de ambiente permite que el control averiguar si debe dibujar con asas de captación.  
  
```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```  
  
### <a name="parameters"></a>Parámetros  
 *pbShowGrabHandles*  
 [out] La dirección de una variable que recibirá el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL siempre devuelve **VARIANT_FALSE** como el valor de esta propiedad.  
  
##  <a name="get_showhatching"></a>IAxWinAmbientDispatch::get_ShowHatching  
 El **ShowHatching** propiedad de ambiente permite que el control averiguar si debe dibujar propio sombreada.  
  
```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```  
  
### <a name="parameters"></a>Parámetros  
 *pbShowHatching*  
 [out] La dirección de una variable que recibirá el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL siempre devuelve **VARIANT_FALSE** como el valor de esta propiedad.  
  
##  <a name="get_usermode"></a>IAxWinAmbientDispatch::get_UserMode  
 El **UserMode** propiedad especifica el modo de usuario de ambiente del contenedor.  
  
```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```  
  
### <a name="parameters"></a>Parámetros  
 *pbUserMode*  
 [out] La dirección de una variable que recibirá el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa `VARIANT_TRUE` como el valor predeterminado de esta propiedad.  
  
##  <a name="put_allowcontextmenu"></a>IAxWinAmbientDispatch::put_AllowContextMenu  
 El **AllowContextMenu** propiedad especifica si el control hospedado tiene permiso para mostrar su propio menú contextual.  
  
```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 *bAllowContextMenu*  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa `VARIANT_TRUE` como el valor predeterminado de esta propiedad.  
  
##  <a name="put_allowshowui"></a>IAxWinAmbientDispatch::put_AllowShowUI  
 El **AllowShowUI** propiedad especifica si el control hospedado tiene permiso para mostrar su propia interfaz de usuario.  
  
```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```  
  
### <a name="parameters"></a>Parámetros  
 *bAllowShowUI*  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa **VARIANT_FALSE** como el valor predeterminado de esta propiedad.  
  
##  <a name="put_allowwindowlessactivation"></a>IAxWinAmbientDispatch::put_AllowWindowlessActivation  
 El **AllowWindowlessActivation** propiedad especifica si el contenedor permitirá la activación sin ventana.  
  
```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```  
  
### <a name="parameters"></a>Parámetros  
 *bAllowWindowless*  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa `VARIANT_TRUE` como el valor predeterminado de esta propiedad.  
  
##  <a name="put_backcolor"></a>IAxWinAmbientDispatch::put_BackColor  
 El `BackColor` propiedad especifica el color de fondo ambiente del contenedor.  
  
```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```  
  
### <a name="parameters"></a>Parámetros  
 *clrBackground*  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa **COLOR_BTNFACE** o **COLOR_WINDOW** como el valor predeterminado de esta propiedad (en función de si el elemento primario de la ventana del host es un cuadro de diálogo o no).  
  
##  <a name="put_displayasdefault"></a>IAxWinAmbientDispatch::put_DisplayAsDefault  
 **DisplayAsDefault** es una propiedad de ambiente que permite que un control averiguar si es el control predeterminado.  
  
```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```  
  
### <a name="parameters"></a>Parámetros  
 `bDisplayAsDefault`  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa **VARIANT_FALSE** como el valor predeterminado de esta propiedad.  
  
##  <a name="put_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::put_DocHostDoubleClickFlags  
 El **DocHostDoubleClickFlags** propiedad especifica la operación que debe tener lugar en respuesta a un doble clic.  
  
```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwDocHostDoubleClickFlags*  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa **DOCHOSTUIDBLCLK_DEFAULT** como el valor predeterminado de esta propiedad.  
  
##  <a name="put_dochostflags"></a>IAxWinAmbientDispatch::put_DocHostFlags  
 El **DocHostFlags** propiedad especifica las funciones de la interfaz de usuario del objeto host.  
  
```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwDocHostFlags*  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa **DOCHOSTUIFLAG_NO3DBORDER** como el valor predeterminado de esta propiedad.  
  
##  <a name="put_font"></a>IAxWinAmbientDispatch::put_Font  
 El **fuente** propiedad especifica la fuente ambiente del contenedor.  
  
```
STDMETHOD(put_Font)(IFontDisp* pFont);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFont`  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa la fuente de la interfaz gráfica de usuario predeterminada o la fuente del sistema como el valor predeterminado de esta propiedad.  
  
##  <a name="put_forecolor"></a>IAxWinAmbientDispatch::put_ForeColor  
 El `ForeColor` propiedad especifica el color de primer plano ambiente del contenedor.  
  
```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```  
  
### <a name="parameters"></a>Parámetros  
 *clrForeground*  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa el color de texto de la ventana de sistema como el valor predeterminado de esta propiedad.  
  
##  <a name="put_localeid"></a>IAxWinAmbientDispatch::put_LocaleID  
 El **LocaleID** propiedad especifica el identificador de configuración regional de ambiente del contenedor.  
  
```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```  
  
### <a name="parameters"></a>Parámetros  
 *lcidLocaleID*  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa el idioma del usuario predeterminado como el valor predeterminado de esta propiedad.  
  
##  <a name="put_messagereflect"></a>IAxWinAmbientDispatch::put_MessageReflect  
 El **MessageReflect** propiedad de ambiente especifica si el contenedor reflejarán los mensajes para el control hospedado.  
  
```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```  
  
### <a name="parameters"></a>Parámetros  
 `bMessageReflect`  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa `VARIANT_TRUE` como el valor predeterminado de esta propiedad.  
  
##  <a name="put_optionkeypath"></a>IAxWinAmbientDispatch::put_OptionKeyPath  
 El **OptionKeyPath** propiedad especifica la ruta de acceso de clave del registro a la configuración de usuario.  
  
```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```  
  
### <a name="parameters"></a>Parámetros  
 *bstrOptionKeyPath*  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="put_usermode"></a>IAxWinAmbientDispatch::put_UserMode  
 El **UserMode** propiedad especifica el modo de usuario de ambiente del contenedor.  
  
```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `bUserMode`  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de objeto de host ATL usa `VARIANT_TRUE` como el valor predeterminado de esta propiedad.  
  
## <a name="see-also"></a>Vea también  
 [Interfaz IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)   
 [Interfaz IAxWinHostWindow (interfaz)](../../atl/reference/iaxwinhostwindow-interface.md)   
 [CAxWindow:: QueryHost](../../atl/reference/caxwindow-class.md#queryhost)   
 [AtlAxGetControl](composite-control-global-functions.md#atlaxgethost)










