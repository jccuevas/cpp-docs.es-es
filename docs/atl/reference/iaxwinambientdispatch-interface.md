---
title: Interfaz IAxWinAmbientDispatch | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinAmbientDispatch
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
translationtype: Machine Translation
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: 2352b970c81f58d164fb47a6d7a4728c708d864a
ms.lasthandoff: 02/24/2017

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
|[get_BackColor](#get_backcolor)|El `BackColor` propiedad especifica el color de fondo de ambiente del contenedor.|  
|[get_DisplayAsDefault](#get_displayasdefault)|**DisplayAsDefault** es una propiedad de ambiente que permite un control para comprobar si se encuentra el control predeterminado.|  
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|El **DocHostDoubleClickFlags** propiedad especifica la operación que se realizará en respuesta a un doble clic.|  
|[get_DocHostFlags](#get_dochostflags)|El **DocHostFlags** propiedad especifica las funciones de la interfaz de usuario del objeto host.|  
|[get_Font](#get_font)|El **fuente** propiedad especifica la fuente de ambiente del contenedor.|  
|[get_ForeColor](#get_forecolor)|El `ForeColor` propiedad especifica el color de primer plano de ambiente del contenedor.|  
|[get_LocaleID](#get_localeid)|El **LocaleID** propiedad especifica el identificador de configuración regional de ambiente del contenedor.|  
|[get_MessageReflect](#get_messagereflect)|El **MessageReflect** propiedad de ambiente especifica si el contenedor reflejarán los mensajes para el control hospedado.|  
|[get_OptionKeyPath](#get_optionkeypath)|El **OptionKeyPath** propiedad especifica la ruta de la clave del registro a la configuración de usuario.|  
|[get_ShowGrabHandles](#get_showgrabhandles)|El **ShowGrabHandles** propiedad de ambiente permite que el control averiguar si debe dibujar con controladores de arrastre.|  
|[get_ShowHatching](#get_showhatching)|El **ShowHatching** propiedad de ambiente permite que el control averiguar si debe dibujarse a sí mismo sombreada.|  
|[get_UserMode](#get_usermode)|El **UserMode** propiedad especifica el modo de usuario de ambiente del contenedor.|  
|[put_AllowContextMenu](#put_allowcontextmenu)|El **AllowContextMenu** propiedad especifica si el control hospedado tiene permiso para mostrar su propio menú contextual.|  
|[put_AllowShowUI](#put_allowshowui)|El **AllowShowUI** propiedad especifica si el control hospedado tiene permiso para mostrar su propia interfaz de usuario.|  
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|El **AllowWindowlessActivation** propiedad especifica si el contenedor permitirá la activación sin ventana.|  
|[put_BackColor](#put_backcolor)|El `BackColor` propiedad especifica el color de fondo de ambiente del contenedor.|  
|[put_DisplayAsDefault](#put_displayasdefault)|**DisplayAsDefault** es una propiedad de ambiente que permite un control para comprobar si se encuentra el control predeterminado.|  
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|El **DocHostDoubleClickFlags** propiedad especifica la operación que se realizará en respuesta a un doble clic.|  
|[put_DocHostFlags](#put_dochostflags)|El **DocHostFlags** propiedad especifica las funciones de la interfaz de usuario del objeto host.|  
|[put_Font](#put_font)|El **fuente** propiedad especifica la fuente de ambiente del contenedor.|  
|[put_ForeColor](#put_forecolor)|El `ForeColor` propiedad especifica el color de primer plano de ambiente del contenedor.|  
|[put_LocaleID](#put_localeid)|El **LocaleID** propiedad especifica el identificador de configuración regional de ambiente del contenedor.|  
|[put_MessageReflect](#put_messagereflect)|El **MessageReflect** propiedad de ambiente especifica si el contenedor reflejarán los mensajes para el control hospedado.|  
|[put_OptionKeyPath](#put_optionkeypath)|El **OptionKeyPath** propiedad especifica la ruta de la clave del registro a la configuración de usuario.|  
|[put_UserMode](#put_usermode)|El **UserMode** propiedad especifica el modo de usuario de ambiente del contenedor.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz expone objetos que hospeda los controles ActiveX de ATL. Llamar a los métodos de esta interfaz para establecer las propiedades de ambientales disponibles en el control hospedado o para especificar otros aspectos del comportamiento del contenedor. Para complementar las propiedades proporcionadas por `IAxWinAmbientDispatch`, utilice [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md).  
  
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
  
##  <a name="a-namegetallowcontextmenua--iaxwinambientdispatchgetallowcontextmenu"></a><a name="get_allowcontextmenu"></a>IAxWinAmbientDispatch::get_AllowContextMenu  
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
 La implementación del objeto host ATL usa `VARIANT_TRUE` como el valor predeterminado de esta propiedad.  
  
##  <a name="a-namegetallowshowuia--iaxwinambientdispatchgetallowshowui"></a><a name="get_allowshowui"></a>IAxWinAmbientDispatch::get_AllowShowUI  
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
 Utiliza la implementación del objeto host ATL **VARIANT_FALSE** como el valor predeterminado de esta propiedad.  
  
##  <a name="a-namegetallowwindowlessactivationa--iaxwinambientdispatchgetallowwindowlessactivation"></a><a name="get_allowwindowlessactivation"></a>IAxWinAmbientDispatch::get_AllowWindowlessActivation  
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
 La implementación del objeto host ATL usa `VARIANT_TRUE` como el valor predeterminado de esta propiedad.  
  
##  <a name="a-namegetbackcolora--iaxwinambientdispatchgetbackcolor"></a><a name="get_backcolor"></a>IAxWinAmbientDispatch::get_BackColor  
 El `BackColor` propiedad especifica el color de fondo de ambiente del contenedor.  
  
```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```  
  
### <a name="parameters"></a>Parámetros  
 *pclrBackground*  
 [out] La dirección de una variable que recibirá el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Utiliza la implementación del objeto host ATL **COLOR_BTNFACE** o **COLOR_WINDOW** como el valor predeterminado de esta propiedad (dependiendo de si el elemento primario de la ventana del host es un cuadro de diálogo o no).  
  
##  <a name="a-namegetdisplayasdefaulta--iaxwinambientdispatchgetdisplayasdefault"></a><a name="get_displayasdefault"></a>IAxWinAmbientDispatch::get_DisplayAsDefault  
 **DisplayAsDefault** es una propiedad de ambiente que permite un control para comprobar si se encuentra el control predeterminado.  
  
```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```  
  
### <a name="parameters"></a>Parámetros  
 *pbDisplayAsDefault*  
 [out] La dirección de una variable que recibirá el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Utiliza la implementación del objeto host ATL **VARIANT_FALSE** como el valor predeterminado de esta propiedad.  
  
##  <a name="a-namegetdochostdoubleclickflagsa--iaxwinambientdispatchgetdochostdoubleclickflags"></a><a name="get_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::get_DocHostDoubleClickFlags  
 El **DocHostDoubleClickFlags** propiedad especifica la operación que se realizará en respuesta a un doble clic.  
  
```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 *pdwDocHostDoubleClickFlags*  
 [out] La dirección de una variable que recibirá el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Utiliza la implementación del objeto host ATL **DOCHOSTUIDBLCLK_DEFAULT** como el valor predeterminado de esta propiedad.  
  
##  <a name="a-namegetdochostflagsa--iaxwinambientdispatchgetdochostflags"></a><a name="get_dochostflags"></a>IAxWinAmbientDispatch::get_DocHostFlags  
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
 Utiliza la implementación del objeto host ATL **DOCHOSTUIFLAG_NO3DBORDER** como el valor predeterminado de esta propiedad.  
  
##  <a name="a-namegetfonta--iaxwinambientdispatchgetfont"></a><a name="get_font"></a>IAxWinAmbientDispatch::get_Font  
 El **fuente** propiedad especifica la fuente de ambiente del contenedor.  
  
```
STDMETHOD(get_Font)(IFontDisp** pFont);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFont`  
 [out] La dirección de un **IFontDisp** puntero de interfaz que se utiliza para recibir el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación del objeto host ATL utiliza la fuente predeterminada de la interfaz gráfica de usuario o la fuente del sistema como el valor predeterminado de esta propiedad.  
  
##  <a name="a-namegetforecolora--iaxwinambientdispatchgetforecolor"></a><a name="get_forecolor"></a>IAxWinAmbientDispatch::get_ForeColor  
 El `ForeColor` propiedad especifica el color de primer plano de ambiente del contenedor.  
  
```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```  
  
### <a name="parameters"></a>Parámetros  
 *pclrForeground*  
 [out] La dirección de una variable que recibirá el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación del objeto host ATL utiliza el color de texto de la ventana de sistema como el valor predeterminado de esta propiedad.  
  
##  <a name="a-namegetlocaleida--iaxwinambientdispatchgetlocaleid"></a><a name="get_localeid"></a>IAxWinAmbientDispatch::get_LocaleID  
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
 La implementación del objeto ATL host usa la configuración regional predeterminada del usuario como el valor predeterminado de esta propiedad.  
  
 Con este método puede detectar el LocalID ambiente, es decir, identificador de configuración regional del programa de control se está usando en. Una vez que conoce el identificador de configuración regional, puede llamar a código para cargar títulos de configuración regional, el texto de mensaje de error, y así sucesivamente desde un archivo de recursos o un archivo DLL satélite.  
  
##  <a name="a-namegetmessagereflecta--iaxwinambientdispatchgetmessagereflect"></a><a name="get_messagereflect"></a>IAxWinAmbientDispatch::get_MessageReflect  
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
 La implementación del objeto host ATL usa `VARIANT_TRUE` como el valor predeterminado de esta propiedad.  
  
##  <a name="a-namegetoptionkeypatha--iaxwinambientdispatchgetoptionkeypath"></a><a name="get_optionkeypath"></a>IAxWinAmbientDispatch::get_OptionKeyPath  
 El **OptionKeyPath** propiedad especifica la ruta de la clave del registro a la configuración de usuario.  
  
```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```  
  
### <a name="parameters"></a>Parámetros  
 *pbstrOptionKeyPath*  
 [out] La dirección de una variable que recibirá el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="a-namegetshowgrabhandlesa--iaxwinambientdispatchgetshowgrabhandles"></a><a name="get_showgrabhandles"></a>IAxWinAmbientDispatch::get_ShowGrabHandles  
 El **ShowGrabHandles** propiedad de ambiente permite que el control averiguar si debe dibujar con controladores de arrastre.  
  
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
  
##  <a name="a-namegetshowhatchinga--iaxwinambientdispatchgetshowhatching"></a><a name="get_showhatching"></a>IAxWinAmbientDispatch::get_ShowHatching  
 El **ShowHatching** propiedad de ambiente permite que el control averiguar si debe dibujarse a sí mismo sombreada.  
  
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
  
##  <a name="a-namegetusermodea--iaxwinambientdispatchgetusermode"></a><a name="get_usermode"></a>IAxWinAmbientDispatch::get_UserMode  
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
 La implementación del objeto host ATL usa `VARIANT_TRUE` como el valor predeterminado de esta propiedad.  
  
##  <a name="a-nameputallowcontextmenua--iaxwinambientdispatchputallowcontextmenu"></a><a name="put_allowcontextmenu"></a>IAxWinAmbientDispatch::put_AllowContextMenu  
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
 La implementación del objeto host ATL usa `VARIANT_TRUE` como el valor predeterminado de esta propiedad.  
  
##  <a name="a-nameputallowshowuia--iaxwinambientdispatchputallowshowui"></a><a name="put_allowshowui"></a>IAxWinAmbientDispatch::put_AllowShowUI  
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
 Utiliza la implementación del objeto host ATL **VARIANT_FALSE** como el valor predeterminado de esta propiedad.  
  
##  <a name="a-nameputallowwindowlessactivationa--iaxwinambientdispatchputallowwindowlessactivation"></a><a name="put_allowwindowlessactivation"></a>IAxWinAmbientDispatch::put_AllowWindowlessActivation  
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
 La implementación del objeto host ATL usa `VARIANT_TRUE` como el valor predeterminado de esta propiedad.  
  
##  <a name="a-nameputbackcolora--iaxwinambientdispatchputbackcolor"></a><a name="put_backcolor"></a>IAxWinAmbientDispatch::put_BackColor  
 El `BackColor` propiedad especifica el color de fondo de ambiente del contenedor.  
  
```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```  
  
### <a name="parameters"></a>Parámetros  
 *clrBackground*  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Utiliza la implementación del objeto host ATL **COLOR_BTNFACE** o **COLOR_WINDOW** como el valor predeterminado de esta propiedad (dependiendo de si el elemento primario de la ventana del host es un cuadro de diálogo o no).  
  
##  <a name="a-nameputdisplayasdefaulta--iaxwinambientdispatchputdisplayasdefault"></a><a name="put_displayasdefault"></a>IAxWinAmbientDispatch::put_DisplayAsDefault  
 **DisplayAsDefault** es una propiedad de ambiente que permite un control para comprobar si se encuentra el control predeterminado.  
  
```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```  
  
### <a name="parameters"></a>Parámetros  
 `bDisplayAsDefault`  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Utiliza la implementación del objeto host ATL **VARIANT_FALSE** como el valor predeterminado de esta propiedad.  
  
##  <a name="a-nameputdochostdoubleclickflagsa--iaxwinambientdispatchputdochostdoubleclickflags"></a><a name="put_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::put_DocHostDoubleClickFlags  
 El **DocHostDoubleClickFlags** propiedad especifica la operación que se realizará en respuesta a un doble clic.  
  
```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwDocHostDoubleClickFlags*  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Utiliza la implementación del objeto host ATL **DOCHOSTUIDBLCLK_DEFAULT** como el valor predeterminado de esta propiedad.  
  
##  <a name="a-nameputdochostflagsa--iaxwinambientdispatchputdochostflags"></a><a name="put_dochostflags"></a>IAxWinAmbientDispatch::put_DocHostFlags  
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
 Utiliza la implementación del objeto host ATL **DOCHOSTUIFLAG_NO3DBORDER** como el valor predeterminado de esta propiedad.  
  
##  <a name="a-nameputfonta--iaxwinambientdispatchputfont"></a><a name="put_font"></a>IAxWinAmbientDispatch::put_Font  
 El **fuente** propiedad especifica la fuente de ambiente del contenedor.  
  
```
STDMETHOD(put_Font)(IFontDisp* pFont);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFont`  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación del objeto host ATL utiliza la fuente predeterminada de la interfaz gráfica de usuario o la fuente del sistema como el valor predeterminado de esta propiedad.  
  
##  <a name="a-nameputforecolora--iaxwinambientdispatchputforecolor"></a><a name="put_forecolor"></a>IAxWinAmbientDispatch::put_ForeColor  
 El `ForeColor` propiedad especifica el color de primer plano de ambiente del contenedor.  
  
```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```  
  
### <a name="parameters"></a>Parámetros  
 *clrForeground*  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación del objeto host ATL utiliza el color de texto de la ventana de sistema como el valor predeterminado de esta propiedad.  
  
##  <a name="a-nameputlocaleida--iaxwinambientdispatchputlocaleid"></a><a name="put_localeid"></a>IAxWinAmbientDispatch::put_LocaleID  
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
 La implementación del objeto ATL host usa la configuración regional predeterminada del usuario como el valor predeterminado de esta propiedad.  
  
##  <a name="a-nameputmessagereflecta--iaxwinambientdispatchputmessagereflect"></a><a name="put_messagereflect"></a>IAxWinAmbientDispatch::put_MessageReflect  
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
 La implementación del objeto host ATL usa `VARIANT_TRUE` como el valor predeterminado de esta propiedad.  
  
##  <a name="a-nameputoptionkeypatha--iaxwinambientdispatchputoptionkeypath"></a><a name="put_optionkeypath"></a>IAxWinAmbientDispatch::put_OptionKeyPath  
 El **OptionKeyPath** propiedad especifica la ruta de la clave del registro a la configuración de usuario.  
  
```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```  
  
### <a name="parameters"></a>Parámetros  
 *bstrOptionKeyPath*  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="a-nameputusermodea--iaxwinambientdispatchputusermode"></a><a name="put_usermode"></a>IAxWinAmbientDispatch::put_UserMode  
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
 La implementación del objeto host ATL usa `VARIANT_TRUE` como el valor predeterminado de esta propiedad.  
  
## <a name="see-also"></a>Vea también  
 [Interfaz IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)   
 [Interfaz IAxWinHostWindow (interfaz)](../../atl/reference/iaxwinhostwindow-interface.md)   
 [CAxWindow:: QueryHost](../../atl/reference/caxwindow-class.md#queryhost)   
 [AtlAxGetControl](http://msdn.microsoft.com/library/ad1f4f16-608d-4e96-8d30-04d4ca906a7b)










