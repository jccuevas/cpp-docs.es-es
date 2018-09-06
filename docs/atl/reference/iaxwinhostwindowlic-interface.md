---
title: IAxWinHostWindowLic (interfaz) | Microsoft Docs
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
ms.openlocfilehash: 849f5269a715013431da2d8b91997c577008bf68
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767096"
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

`IAxWinHostWindowLic` hereda de [IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) y agrega los métodos que admiten la creación de controles con licencia.

Consulte [hospeda controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa los miembros de esta interfaz.

## <a name="requirements"></a>Requisitos

La definición de esta interfaz está disponible como IDL o C++, como se muestra a continuación.

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

*bstrLic*  
[in] BSTR que contiene la clave de licencia para el control.

### <a name="remarks"></a>Comentarios

Consulte [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol) para obtener una descripción de los parámetros restantes y el valor devuelto.

Llamar a este método equivale a llamar a [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Ejemplo

Consulte [hospeda controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `IAxWinHostWindowLic::CreateControlLic`.

##  <a name="createcontrollicex"></a>  IAxWinHostWindowLic::CreateControlLicEx

Crea un control ActiveX con licencia, lo inicializa y lo hospeda en la ventana especificada, de forma similar a [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol).

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

Consulte [IAxWinHostWindow::CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex) para obtener una descripción de los parámetros restantes y el valor devuelto.

### <a name="example"></a>Ejemplo

Consulte [hospeda controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `IAxWinHostWindowLic::CreateControlLicEx`.

