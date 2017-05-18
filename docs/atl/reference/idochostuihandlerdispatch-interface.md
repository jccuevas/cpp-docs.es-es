---
title: Interfaz IDocHostUIHandlerDispatch | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
dev_langs:
- C++
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
caps.latest.revision: 22
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
ms.sourcegitcommit: 8232df949d3bdcbaab16af1802d7275a9a8642f3
ms.openlocfilehash: a8765f5191ea2101dc20985e8112e3e06ccd6da0
ms.contentlocale: es-es
ms.lasthandoff: 03/30/2017

---
# <a name="idochostuihandlerdispatch-interface"></a>Interfaz IDocHostUIHandlerDispatch
Una interfaz para el análisis de HTML de Microsoft y el motor de representación.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```
interface IDocHostUIHandlerDispatch : IDispatch
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
> [!NOTE]
>  Los vínculos en la tabla siguiente son los temas de referencia de INet SDK para los miembros de la [IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx) interfaz. `IDocHostUIHandlerDispatch`tiene la misma funcionalidad que **IDocUIHostHandler**, con la diferencia es que `IDocHostUIHandlerDispatch` es una interfaz dispinterface mientras que **IDocUIHostHandler** es una interfaz personalizada.  
  
|||  
|-|-|  
|[EnableModeless](https://msdn.microsoft.com/library/aa753253.aspx)|Se invoca desde MSHTML implementación de [IOleInPlaceActiveObject::EnableModeless](http://msdn.microsoft.com/library/windows/desktop/ms680115). También se llama cuando MSHTML muestra la interfaz de usuario modal.|  
|[FilterDataObject](https://msdn.microsoft.com/library/aa753254.aspx)|Se llama en el host MSHTML para permitir que el host reemplazar el objeto de datos MSHTML.|  
|[GetDropTarget](https://msdn.microsoft.com/library/aa753255.aspx)|Lo llama MSHTML cuando está usándola como un destino para colocar para permitir que el host proporcione una alternativa [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679).|  
|[GetExternal](https://msdn.microsoft.com/library/aa753256.aspx)|Llama a MSHTML para obtener la interfaz del host IDispatch.|  
|[GetHostInfo](https://msdn.microsoft.com/library/aa753257.aspx)|Recupera las capacidades de la interfaz de usuario de host MSHTML.|  
|[GetOptionKeyPath](https://msdn.microsoft.com/library/aa753258.aspx)|Devuelve la clave del registro bajo la que MSHTML almacena las preferencias del usuario.|  
|[HideUI](https://msdn.microsoft.com/library/aa753259.aspx)|Se llama cuando MSHTML quita sus menús y barras de herramientas.|  
|[OnDocWindowActivate](https://msdn.microsoft.com/library/aa753261.aspx)|Se invoca desde MSHTML implementación de [IOleInPlaceActiveObject:: OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281).|  
|[OnFrameWindowActivate](https://msdn.microsoft.com/library/aa753262.aspx)|Se invoca desde MSHTML implementación de [IOleInPlaceActiveObject:: Onframewindowactivate](http://msdn.microsoft.com/library/windows/desktop/ms683969).|  
|[ResizeBorder](https://msdn.microsoft.com/library/aa753263.aspx)|Se invoca desde MSHTML implementación de [IOleInPlaceActiveObject::](http://msdn.microsoft.com/library/windows/desktop/ms680053).|  
|[ShowContextMenu](https://msdn.microsoft.com/library/aa753264.aspx)|Llamar desde MSHTML para mostrar un menú contextual.|  
|[ShowUI](https://msdn.microsoft.com/library/aa753265.aspx)|Permite al host reemplazan a las barras de herramientas y menús MSHTML.|  
|[TranslateAccelerator](https://msdn.microsoft.com/library/aa753266.aspx)|Llama a MSHTML cuando [IOleInPlaceActiveObject:: TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360) o [IOleControlSite:: TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693756) se llama.|  
|[TranslateUrl](https://msdn.microsoft.com/library/aa753267.aspx)|Llama a MSHTML para ofrecer al host la oportunidad de modificar la dirección URL que va a cargarse.|  
|[UpdateUI](https://msdn.microsoft.com/library/aa753268.aspx)|Notifica al host que cambió el estado del comando.|  
  
## <a name="remarks"></a>Comentarios  
 Un host puede reemplazar los menús, barras de herramientas y menús contextuales usados por el análisis de HTML de Microsoft y el motor de representación (MSHTML) mediante la implementación de esta interfaz.  
  
## <a name="requirements"></a>Requisitos  
 La definición de esta interfaz está disponible como IDL o C++, tal y como se muestra a continuación.  
  
|Tipo de definición|Archivo|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h (que también se incluye en ATLBase.h)|  
  
## <a name="see-also"></a>Vea también  
 [IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx)










