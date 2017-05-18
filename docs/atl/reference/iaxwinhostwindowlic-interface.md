---
title: Interfaz IAxWinHostWindowLic | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinHostWindowLic
- No header/ATL::IAxWinHostWindowLic
- No header/ATL::CreateControlLic
- No header/ATL::CreateControlLicEx
dev_langs:
- C++
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
caps.latest.revision: 19
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
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: 01ff8a7205418583606cbfdb1c028d7097501e00
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="iaxwinhostwindowlic-interface"></a>IAxWinHostWindowLic (interfaz)
Esta interfaz proporciona métodos para manipular un control con licencia y su objeto de host.  
  
## <a name="syntax"></a>Sintaxis  
  
```
interface IAxWinHostWindowLic : IAxWinHostWindow
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[CreateControlLic](#createcontrollic)|Crea un control con licencia y lo adjunta al objeto host.|  
|[CreateControlLicEx](#createcontrollicex)|Crea un control con licencia, se adjunta al objeto host y, opcionalmente, establece un controlador de eventos.|  
  
## <a name="remarks"></a>Comentarios  
 `IAxWinHostWindowLic`hereda de [interfaz IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) y agrega métodos que admiten la creación de controles con licencia.  
  
 Consulte [hospeda controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que utiliza los miembros de esta interfaz.  
  
## <a name="requirements"></a>Requisitos  
 La definición de esta interfaz está disponible como archivo IDL o C++, como se muestra a continuación.  
  
|Tipo de definición|Archivo|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h (que también se incluye en ATLBase.h)|  
  
##  <a name="createcontrollic"></a>IAxWinHostWindowLic::CreateControlLic  
 Crea un control con licencia, lo inicializa y lo hospeda en la ventana identificada por `hWnd`.  
  
```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```  
  
### <a name="parameters"></a>Parámetros  
 `bstrLic`  
 [in] BSTR que contiene la clave de licencia para el control.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol) para obtener una descripción de los demás parámetros y valor devuelto.  
  
 Llamar a este método equivale a llamar a [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)  
  
### <a name="example"></a>Ejemplo  
 Consulte [hospeda controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `IAxWinHostWindowLic::CreateControlLic`.  
  
##  <a name="createcontrollicex"></a>IAxWinHostWindowLic::CreateControlLicEx  
 Crea un control ActiveX con licencia, lo inicializa y lo hospeda en la ventana especificada, similar a [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol).  
  
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
 `bstrLic`  
 [in] BSTR que contiene la clave de licencia para el control.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IAxWinHostWindow::CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex) para obtener una descripción de los demás parámetros y valor devuelto.  
  
### <a name="example"></a>Ejemplo  
 Consulte [hospeda controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `IAxWinHostWindowLic::CreateControlLicEx`.










