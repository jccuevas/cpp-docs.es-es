---
title: IDocHostUIHandlerDispatch (interfaz)
ms.date: 11/04/2016
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: 6ce3532e99dc1d0ff0151285766aa5d78c2b9e9d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275313"
---
# <a name="idochostuihandlerdispatch-interface"></a>IDocHostUIHandlerDispatch (interfaz)

Interfaz para el análisis de HTML de Microsoft y el motor de representación.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

> [!NOTE]
>  Los vínculos de la tabla siguiente son los temas de referencia de INet SDK para los miembros de la [IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx) interfaz. `IDocHostUIHandlerDispatch` tiene la misma funcionalidad que `IDocUIHostHandler`, con la diferencia que `IDocHostUIHandlerDispatch` es una interfaz dispinterface mientras que `IDocUIHostHandler` es una interfaz personalizada.

|||
|-|-|
|[EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|Se llama desde la implementación de MSHTML de [IOleInPlaceActiveObject::EnableModeless](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless). También se llama cuando MSHTML muestra la interfaz de usuario modal.|
|[FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|Se llama en el host MSHTML para permitir que el host reemplazar el objeto de datos de MSHTML.|
|[GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|Lo llama MSHTML cuando lo está usando como un destino de colocación para permitir que el host proporcione una alternativa [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget).|
|[GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|Lo llama MSHTML para obtener la interfaz de IDispatch del host.|
|[GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|Recupera las capacidades de la interfaz de usuario de host MSHTML.|
|[GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|Devuelve la clave del registro bajo la que MSHTML almacena las preferencias del usuario.|
|[HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|Se llama cuando MSHTML quita sus menús y barras de herramientas.|
|[OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|Se llama desde la implementación de MSHTML de [IOleInPlaceActiveObject:: OnDocWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate).|
|[OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|Se llama desde la implementación de MSHTML de [IOleInPlaceActiveObject:: Onframewindowactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate).|
|[ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|Se llama desde la implementación de MSHTML de [IOleInPlaceActiveObject::](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder).|
|[ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|Se llama para mostrar un menú contextual de Mshtml.|
|[ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|Permite al host reemplazar las barras de herramientas y menús MSHTML.|
|[TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|Lo llama MSHTML cuando [IOleInPlaceActiveObject:: TranslateAccelerator](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) o [IOleControlSite:: TranslateAccelerator](/windows/desktop/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator) se llama.|
|[TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|Lo llama MSHTML para permitir que el host de una oportunidad modificar la dirección URL se va a cargar.|
|[UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|Notifica al host que cambió el estado del comando.|

## <a name="remarks"></a>Comentarios

Un host puede reemplazar los menús, barras de herramientas y menús contextuales utilizados por el análisis de HTML de Microsoft y el motor de representación (MSHTML) implementando esta interfaz.

## <a name="requirements"></a>Requisitos

La definición de esta interfaz está disponible como IDL o C++, como se muestra a continuación.

|Tipo de definición|Archivo|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|ATLIFace.h (que también se incluye en ATLBase.h)|

## <a name="see-also"></a>Vea también

[IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx)
