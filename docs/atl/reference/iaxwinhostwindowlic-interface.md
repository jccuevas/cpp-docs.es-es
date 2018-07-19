---
title: Interfaz IAxWinHostWindowLic | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
dev_langs:
- C++
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41b4d7891d1bb00f4ee689477d1056dbf2bf28cf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362845"
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
|[CreateControlLicEx](#createcontrollicex)|Crea un control con licencia, se adjunta al objeto host y, opcionalmente, configura un controlador de eventos.|  
  
## <a name="remarks"></a>Comentarios  
 `IAxWinHostWindowLic` hereda de [interfaces IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) y agrega los métodos que permiten la creación de controles con licencia.  
  
 Vea [hospedaje de controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que utiliza los miembros de esta interfaz.  
  
## <a name="requirements"></a>Requisitos  
 La definición de esta interfaz está disponible como IDL o C++, tal y como se muestra a continuación.  
  
|Tipo de definición|Archivo|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h (que también se incluye en ATLBase.h)|  
  
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
 `bstrLic`  
 [in] El objeto BSTR que contiene la clave de licencia para el control.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol) para obtener una descripción de los parámetros restantes y valor devuelto.  
  
 Llamar a este método equivale a llamar a [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)  
  
### <a name="example"></a>Ejemplo  
 Vea [hospedaje de controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `IAxWinHostWindowLic::CreateControlLic`.  
  
##  <a name="createcontrollicex"></a>  IAxWinHostWindowLic::CreateControlLicEx  
 Crea un control ActiveX con licencia, lo inicializa y lo hospeda en la ventana especificada, tal como [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol).  
  
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
 [in] El objeto BSTR que contiene la clave de licencia para el control.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IAxWinHostWindow::CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex) para obtener una descripción de los parámetros restantes y valor devuelto.  
  
### <a name="example"></a>Ejemplo  
 Vea [hospedaje de controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `IAxWinHostWindowLic::CreateControlLicEx`.









