---
title: IDocHostUIHandlerDispatch (interfaz) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
dev_langs:
- C++
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 936d9b30f18f5ef84c68c55a1607cfcd88d45525
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884618"
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
|[EnableModeless](https://msdn.microsoft.com/library/aa753253.aspx)|Se llama desde la implementación de MSHTML de [IOleInPlaceActiveObject::EnableModeless](http://msdn.microsoft.com/library/windows/desktop/ms680115). También se llama cuando MSHTML muestra la interfaz de usuario modal.|  
|[FilterDataObject](https://msdn.microsoft.com/library/aa753254.aspx)|Se llama en el host MSHTML para permitir que el host reemplazar el objeto de datos de MSHTML.|  
|[GetDropTarget](https://msdn.microsoft.com/library/aa753255.aspx)|Lo llama MSHTML cuando lo está usando como un destino de colocación para permitir que el host proporcione una alternativa [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679).|  
|[GetExternal](https://msdn.microsoft.com/library/aa753256.aspx)|Lo llama MSHTML para obtener la interfaz de IDispatch del host.|  
|[GetHostInfo](https://msdn.microsoft.com/library/aa753257.aspx)|Recupera las capacidades de la interfaz de usuario de host MSHTML.|  
|[GetOptionKeyPath](https://msdn.microsoft.com/library/aa753258.aspx)|Devuelve la clave del registro bajo la que MSHTML almacena las preferencias del usuario.|  
|[HideUI](https://msdn.microsoft.com/library/aa753259.aspx)|Se llama cuando MSHTML quita sus menús y barras de herramientas.|  
|[OnDocWindowActivate](https://msdn.microsoft.com/library/aa753261.aspx)|Se llama desde la implementación de MSHTML de [IOleInPlaceActiveObject:: OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281).|  
|[OnFrameWindowActivate](https://msdn.microsoft.com/library/aa753262.aspx)|Se llama desde la implementación de MSHTML de [IOleInPlaceActiveObject:: Onframewindowactivate](http://msdn.microsoft.com/library/windows/desktop/ms683969).|  
|[ResizeBorder](https://msdn.microsoft.com/library/aa753263.aspx)|Se llama desde la implementación de MSHTML de [IOleInPlaceActiveObject::](http://msdn.microsoft.com/library/windows/desktop/ms680053).|  
|[ShowContextMenu](https://msdn.microsoft.com/library/aa753264.aspx)|Se llama para mostrar un menú contextual de Mshtml.|  
|[ShowUI](https://msdn.microsoft.com/library/aa753265.aspx)|Permite al host reemplazar las barras de herramientas y menús MSHTML.|  
|[TranslateAccelerator](https://msdn.microsoft.com/library/aa753266.aspx)|Lo llama MSHTML cuando [IOleInPlaceActiveObject:: TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360) o [IOleControlSite:: TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693756) se llama.|  
|[TranslateUrl](https://msdn.microsoft.com/library/aa753267.aspx)|Lo llama MSHTML para permitir que el host de una oportunidad modificar la dirección URL se va a cargar.|  
|[UpdateUI](https://msdn.microsoft.com/library/aa753268.aspx)|Notifica al host que cambió el estado del comando.|  
  
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









