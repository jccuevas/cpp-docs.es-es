---
title: Interfaz IDocHostUIHandlerDispatch
ms.date: 07/02/2019
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: b7072b80b738aa12635427a2604b38fb3585b452
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329723"
---
# <a name="idochostuihandlerdispatch-interface"></a>Interfaz IDocHostUIHandlerDispatch

Una interfaz para el motor de representación y análisis HTML de Microsoft.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

> [!NOTE]
> Los vínculos de la tabla siguiente son a los temas de referencia del SDK de INet para los miembros de la interfaz [IDocUIHostHandler.](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\)) `IDocHostUIHandlerDispatch`tiene la misma `IDocUIHostHandler`funcionalidad que , `IDocHostUIHandlerDispatch` con la diferencia `IDocUIHostHandler` es que es una interfaz dispinterface mientras que es una interfaz personalizada.

|||
|-|-|
|[EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|Llamado desde la implementación de MSHTML de [IOleInPlaceActiveObject::EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless). También se llama cuando MSHTML muestra la interfaz de usuario modal.|
|[FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|Llamado en el host por MSHTML para permitir que el host reemplace el objeto de datos de MSHTML.|
|[GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|Llamado por MSHTML cuando se utiliza como destino de colocación para permitir que el host proporcione un [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)alternativo.|
|[GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|Llamado por MSHTML para obtener la interfaz IDispatch del host.|
|[GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|Recupera las capacidades de interfaz de usuario del host MSHTML.|
|[GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|Devuelve la clave del Registro en la que MSHTML almacena las preferencias del usuario.|
|[HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|Se llama cuando MSHTML quita sus menús y barras de herramientas.|
|[OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|Llamado desde la implementación MSHTML de [IOleInPlaceActiveObject::OnDocWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate).|
|[OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|Llamado desde la implementación MSHTML de [IOleInPlaceActiveObject::OnFrameWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate).|
|[ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|Se llama desde la implementación de MSHTML de [IOleInPlaceActiveObject::ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder).|
|[ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|Se llama desde MSHTML para mostrar un menú contextual.|
|[ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|Permite que el host reemplace los menús y barras de herramientas MSHTML.|
|[TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|Llamado por MSHTML cuando [IOleInPlaceActiveObject::TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) o [IOleControlSite::TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator) se llama.|
|[TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|Llamado por MSHTML para permitir al host una oportunidad de modificar la dirección URL que se va a cargar.|
|[UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|Notifica al host que cambió el estado del comando.|

## <a name="remarks"></a>Observaciones

Un host puede reemplazar los menús, barras de herramientas y menús contextuales utilizados por el motor de representación y análisis HTML de Microsoft (MSHTML) mediante la implementación de esta interfaz.

## <a name="requirements"></a>Requisitos

La definición de esta interfaz está disponible como IDL o C++, como se muestra a continuación.

|Tipo de definición|Archivo|
|---------------------|----------|
|Idl|ATLIFace.idl|
|C++|ATLIFace.h (también incluido en ATLBase.h)|

## <a name="see-also"></a>Consulte también

[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))
