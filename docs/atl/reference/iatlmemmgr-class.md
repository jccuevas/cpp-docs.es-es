---
title: IAtlMemMgr (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IAtlMemMgr
- ATLMEM/ATL::IAtlMemMgr
- ATLMEM/ATL::Allocate
- ATLMEM/ATL::Free
- ATLMEM/ATL::GetSize
- ATLMEM/ATL::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- IAtlMemMgr class
- memory, managing
- memory, memory manager
ms.assetid: 18b2c569-25fe-4464-bdb6-3b1abef7154a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d623df9fcab776a42fda7ca13269554b9f38b56c
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880578"
---
# <a name="iatlmemmgr-class"></a>IAtlMemMgr (clase)
Esta clase representa la interfaz a un administrador de memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[asignar](#allocate)|Llame a este método para asignar un bloque de memoria.|  
|[gratis](#free)|Llame a este método para liberar un bloque de memoria.|  
|[GetSize](#getsize)|Llame a este método para recuperar el tamaño de un bloque de memoria asignado.|  
|[Reasignar](#reallocate)|Llame a este método para volver a asignar un bloque de memoria.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se implementa mediante [CComHeap](../../atl/reference/ccomheap-class.md), [CCRTHeap](../../atl/reference/ccrtheap-class.md), [CLocalHeap](../../atl/reference/clocalheap-class.md), [CGlobalHeap](../../atl/reference/cglobalheap-class.md), o [CWin32Heap](../../atl/reference/cwin32heap-class.md).  
  
> [!NOTE]
>  Las funciones del montón local y global son más lentas que otras funciones de administración de memoria y no proporcionan tantas características. Por lo tanto, las aplicaciones nuevas deben usar el [funciones de montón](http://msdn.microsoft.com/library/windows/desktop/aa366711). Están disponibles en el [CWin32Heap](../../atl/reference/cwin32heap-class.md) clase.  
  
## <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlmem.h  
  
##  <a name="allocate"></a>  IAtlMemMgr::Allocate  
 Llame a este método para asignar un bloque de memoria.  
  
```
void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *nBytes*  
 Número de bytes solicitado en el nuevo bloque de memoria.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero al principio del bloque de memoria recién asignado.  
  
### <a name="remarks"></a>Comentarios  
 Llame a [IAtlMemMgr::Free](#free) o [IAtlMemMgr::Reallocate](#reallocate) para liberar la memoria asignada por este método.  
  
### <a name="example"></a>Ejemplo  
 Para obtener un ejemplo, vea el [IAtlMemMgr Introducción](../../atl/reference/iatlmemmgr-class.md).  
  
##  <a name="free"></a>  IAtlMemMgr::Free  
 Llame a este método para liberar un bloque de memoria.  
  
```
void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *p*  
 Puntero a la memoria previamente asignada por este administrador de memoria.  
  
### <a name="remarks"></a>Comentarios  
 Use este método para liberar la memoria obtenida por [IAtlMemMgr::Allocate](#allocate) o [IAtlMemMgr::Reallocate](#reallocate).  
  
### <a name="example"></a>Ejemplo  
 Para obtener un ejemplo, vea el [IAtlMemMgr Introducción](../../atl/reference/iatlmemmgr-class.md).  
  
##  <a name="getsize"></a>  IAtlMemMgr::GetSize  
 Llame a este método para recuperar el tamaño de un bloque de memoria asignado.  
  
```
size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *p*  
 Puntero a la memoria previamente asignada por este administrador de memoria.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el tamaño del bloque de memoria en bytes.  
  
### <a name="example"></a>Ejemplo  
 Para obtener un ejemplo, vea el [IAtlMemMgr Introducción](../../atl/reference/iatlmemmgr-class.md).  
  
##  <a name="reallocate"></a>  IAtlMemMgr::Reallocate  
 Llame a este método para reasignar la memoria asignada por este administrador de memoria.  
  
```
void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *p*  
 Puntero a la memoria previamente asignada por este administrador de memoria.  
  
 *nBytes*  
 Número de bytes solicitado en el nuevo bloque de memoria.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero al principio del bloque de memoria recién asignado.  
  
### <a name="remarks"></a>Comentarios  
 Llame a [IAtlMemMgr::Free](#free) o [IAtlMemMgr::Reallocate](#reallocate) para liberar la memoria asignada por este método.  
  
 Conceptualmente, este método libera la memoria existente y asigna un nuevo bloque de memoria. En realidad, es posible que se amplíe o reutilizar en caso contrario, la memoria existente.  
  
### <a name="example"></a>Ejemplo  
 Para obtener un ejemplo, vea el [IAtlMemMgr Introducción](../../atl/reference/iatlmemmgr-class.md).  
  
##  <a name="get_allowcontextmenu"></a>  IAxWinAmbientDispatch::get_AllowContextMenu  
 El `AllowContextMenu` propiedad especifica si el control hospedado se puede mostrar su propio menú contextual.  
  
```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 *pbAllowContextMenu*  
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
 *pbAllowShowUI*  
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
 *pbAllowWindowless*  
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
 *pclrBackground*  
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
 *pbDisplayAsDefault*  
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
 *pdwDocHostDoubleClickFlags*  
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
 *pdwDocHostFlags*  
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
 *pFont*  
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
 *pclrForeground*  
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
 *plcidLocaleID*  
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
 *pbMessageReflect*  
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
 *pbstrOptionKeyPath*  
 [out] La dirección de una variable que recibirá el valor actual de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
##  <a name="get_showgrabhandles"></a>  IAxWinAmbientDispatch::get_ShowGrabHandles  
 El `ShowGrabHandles` propiedad ambiente permite que el control averiguar si debe dibujar con controladores de arrastre.  
  
```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```  
  
### <a name="parameters"></a>Parámetros  
 *pbShowGrabHandles*  
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
 *pbShowHatching*  
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
 *pbUserMode*  
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
 *bAllowContextMenu*  
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
 *bAllowShowUI*  
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
 *bAllowWindowless*  
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
 *clrBackground*  
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
 *bDisplayAsDefault*  
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
 *dwDocHostDoubleClickFlags*  
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
 *dwDocHostFlags*  
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
 *pFont*  
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
 *clrForeground*  
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
 *lcidLocaleID*  
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
 *bMessageReflect*  
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
 *bstrOptionKeyPath*  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
##  <a name="put_usermode"></a>  IAxWinAmbientDispatch::put_UserMode  
 El `UserMode` propiedad especifica el modo de usuario de ambiente del contenedor.  
  
```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```  
  
### <a name="parameters"></a>Parámetros  
 *bUserMode*  
 [in] El nuevo valor de esta propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación del objeto host ATL utiliza VARIANT_TRUE como el valor predeterminado de esta propiedad.  
  
##  <a name="setambientdispatch"></a>  IAxWinAmbientDispatchEx::SetAmbientDispatch  
 Este método se llama para complementar la interfaz de la propiedad de ambiente predeterminada con una interfaz definida por el usuario.  
  
```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 *pDispatch*  
 Puntero a la nueva interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `SetAmbientDispatch` se denomina con un puntero a una nueva interfaz, se usará esta nueva interfaz para invocar las propiedades o métodos más frecuentes para el control hospedado, si dichas propiedades no se han proporcionado por [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).  
  
##  <a name="attachcontrol"></a>  IAxWinHostWindow:: AttachControl  
 Asocia un control existente (e inicializado anteriormente) al objeto host mediante la ventana identificada por *hWnd*.  
  
```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 *pUnkControl*  
 [in] Un puntero a la `IUnknown` interfaz del control que se adjuntará al objeto host.  
  
 *hWnd*  
 [in] Identificador de la ventana que se usará para hospedar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
##  <a name="createcontrol"></a>  IAxWinHostWindow::CreateControl  
 Crea un control, lo inicializa y lo hospeda en la ventana identificada por *hWnd*.  
  
```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpTricsData*  
 [in] Cadena que identifica el control que se va a crear. Puede ser un CLSID (incluidas las llaves), ProgID, dirección URL o HTML sin formato (precedida por **MSHTML:**).  
  
 *hWnd*  
 [in] Identificador de la ventana que se usará para hospedar.  
  
 *pStream*  
 [in] Un puntero de interfaz para una secuencia que contiene los datos de inicialización para el control. Puede ser NULL.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 El objeto host exponer esta interfaz para que los mensajes se pueden reflejar en el control y otras características del contenedor funcionará se pueden crear subclases de esta ventana.  
  
 Llamar a este método equivale a llamar a [IAxWinHostWindow::CreateControlEx](#createcontrolex).  
  
 Para crear un control ActiveX con licencia, consulte [IAxWinHostWindowLic::CreateControlLic](#createcontrollicex).  
  
##  <a name="createcontrolex"></a>  IAxWinHostWindow::CreateControlEx  
 Crea un control ActiveX, lo inicializa y lo hospeda en la ventana especificada, de forma similar a [IAxWinHostWindow::CreateControl](#createcontrol).  
  
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
 *lpTricsData*  
 [in] Cadena que identifica el control que se va a crear. Puede ser un CLSID (incluidas las llaves), ProgID, dirección URL o HTML sin formato (con el prefijo **MSHTML:**).  
  
 *hWnd*  
 [in] Identificador de la ventana que se usará para hospedar.  
  
 *pStream*  
 [in] Un puntero de interfaz para una secuencia que contiene los datos de inicialización para el control. Puede ser NULL.  
  
 *ppUnk*  
 [out] La dirección de un puntero que va a recibir el `IUnknown` interfaz del control creado. Puede ser NULL.  
  
 *riidAdvise*  
 [in] Identificador de interfaz de una interfaz de salida en el objeto contenido. Puede ser IID_NULL.  
  
 *punkAdvise*  
 [in] Un puntero a la `IUnknown` interfaz del objeto receptor para estar conectado al punto de conexión en el objeto contenido especificado por `iidSink`.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 A diferencia de la `CreateControl` método `CreateControlEx` también permite recibir un puntero de interfaz al control recién creado y configurado un receptor de eventos para recibir eventos desencadenados por el control.  
  
 Para crear un control ActiveX con licencia, consulte [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex).  
  
##  <a name="querycontrol"></a>  IAxWinHostWindow::QueryControl  
 Devuelve el puntero de interfaz especificado proporcionado por el control hospedado.  
  
```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parámetros  
 *riid*  
 [in] El identificador de una interfaz en el control que se solicita.  
  
 *ppvObject*  
 [out] La dirección de un puntero que va a recibir la interfaz especificada del control creado.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
##  <a name="setexternaldispatch"></a>  IAxWinHostWindow::SetExternalDispatch  
 Establece la interfaz dispinterface externa, que está disponible para los controles contenidos a través de la [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) método.  
  
```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDisp*  
 [in] Un puntero a un `IDispatch` interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
##  <a name="setexternaluihandler"></a>  IAxWinHostWindow::SetExternalUIHandler  
 Llame a esta función para establecer la externa [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) interfaz para el `CAxWindow` objeto.  
  
```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDisp*  
 [in] Un puntero a un `IDocHostUIHandlerDispatch` interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se usa los controles (por ejemplo, el control del explorador Web) que consulta el sitio del host para el `IDocHostUIHandlerDispatch` interfaz.  
  
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
 *bstrLic*  
 [in] BSTR que contiene la clave de licencia para el control.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IAxWinHostWindow::CreateControl](#createcontrol) para obtener una descripción de los parámetros restantes y el valor devuelto.  
  
 Llamar a este método equivale a llamar a [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)  
  
### <a name="example"></a>Ejemplo  
 Consulte [hospeda controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `IAxWinHostWindowLic::CreateControlLic`.  
  
##  <a name="createcontrollicex"></a>  IAxWinHostWindowLic::CreateControlLicEx  
 Crea un control ActiveX con licencia, lo inicializa y lo hospeda en la ventana especificada, de forma similar a [IAxWinHostWindow::CreateControl](#createcontrol).  
  
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
 *bstrLic*  
 [in] BSTR que contiene la clave de licencia para el control.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IAxWinHostWindow::CreateControlEx](#createcontrolex) para obtener una descripción de los parámetros restantes y el valor devuelto.  
  
### <a name="example"></a>Ejemplo  
 Consulte [hospeda controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `IAxWinHostWindowLic::CreateControlLicEx`.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
