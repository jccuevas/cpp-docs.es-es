---
title: Clase CWinTraits | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinTraits
- CMDIChildWinTraits
- ATL.CWinTraits
- CFrameWinTraits
- ATL::CWinTraits
- CControlWinTraits
dev_langs:
- C++
helpviewer_keywords:
- CMDIChildWinTraits class
- window styles, default values for ATL
- CWinTraits class
- CFrameWinTraits class
- CControlWinTraits class
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: abd62b916f976721bf85fc4bb2a94ffaf5b217ea
ms.lasthandoff: 02/24/2017

---
# <a name="cwintraits-class"></a>Clase CWinTraits
Esta clase proporciona un método para estandarizar los estilos utilizados al crear un objeto de ventana.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <DWORD t_dwStyle = 0, DWORD t_dwExStyle = 0>  class CWinTraits
```  
  
#### <a name="parameters"></a>Parámetros  
 `t_dwStyle`  
 Estilos de ventana estándar de manera predeterminada.  
  
 `t_dwExStyle`  
 De forma predeterminada, los estilos de ventana extendidos.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWinTraits::GetWndExStyle](#getwndexstyle)|(Estático) Recupera los estilos extendidos para el `CWinTraits` objeto.|  
|[CWinTraits::GetWndStyle](#getwndstyle)|(Estático) Recupera los estilos estándar para la `CWinTraits` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Esto [rasgos de las ventanas](../../atl/understanding-window-traits.md) clase proporciona un método sencillo de estandarizar los estilos utilizados para la creación de un objeto de ventana ATL. Usar una especialización de esta clase como un parámetro de plantilla a [CWindowImpl](../../atl/reference/cwindowimpl-class.md) u otra de las clases de ventana de ATL para especificar los estilos predeterminados estándar y extendidos utilizados para instancias de esa clase de ventana.  
  
 Use esta plantilla cuando desee proporcionar predeterminado estilos de ventana que se utilizará sólo cuando no hay otros estilos especificados en la llamada a [CWindowImpl:: Create](../../atl/reference/cwindowimpl-class.md#create).  
  
 ATL proporciona tres especializaciones predefinidas de esta plantilla para combinaciones utilizadas de estilos de ventana:  
  
 `CControlWinTraits`  
 Diseñado para una ventana de control estándar. Se utilizan los siguientes estilos estándares: **WS_CHILD**, **WS_VISIBLE**, **WS_CLIPCHILDREN**, y **WS_CLIPSIBLINGS**. No hay ningún estilos extendidos.  
  
 `CFrameWinTraits`  
 Diseñado para una ventana de marco estándar. Incluyen los estilos estándares utilizados: **WS_OVERLAPPEDWINDOW**, **WS_CLIPCHILDREN**, y **WS_CLIPSIBLINGS**. Los estilos extendidos utilizados incluyen: **WS_EX_APPWINDOW** y **WS_EX_WINDOWEDGE**.  
  
 `CMDIChildWinTraits`  
 Diseñado para una ventana secundaria MDI estándar. Incluyen los estilos estándares utilizados: **WS_OVERLAPPEDWINDOW**, **WS_CHILD**, **WS_VISIBLE**, **WS_CLIPCHILDREN**, y **WS_CLIPSIBLINGS**. Los estilos extendidos utilizados incluyen: **WS_EX_MDICHILD**.  
  
 Si desea asegurarse de que determinados estilos para todas las instancias de la clase de ventana al tiempo que permite a otros estilos a establecerse en una base por instancia, use [CWinTraitsOR](../../atl/reference/cwintraitsor-class.md) en su lugar.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
  
##  <a name="a-namegetwndstylea--cwintraitsgetwndstyle"></a><a name="getwndstyle"></a>CWinTraits::GetWndStyle  
 Llame a esta función para recuperar los estilos estándar de la `CWinTraits` objeto.  
  
```
static DWORD GetWndStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Estilos utilizados para la creación de una ventana estándar. Si `dwStyle` es 0, los valores de estilo de plantilla ( `t_dwStyle`) se devuelven. Si `dwStyle` es distinto de cero, `dwStyle` se devuelve.  
  
### <a name="return-value"></a>Valor devuelto  
 Los estilos de ventana estándar del objeto.  
  
##  <a name="a-namegetwndexstylea--cwintraitsgetwndexstyle"></a><a name="getwndexstyle"></a>CWinTraits::GetWndExStyle  
 Llame a esta función para recuperar los estilos extendidos de la `CWinTraits` objeto.  
  
```
static DWORD GetWndExStyle(DWORD dwExStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwExStyle`  
 Estilos extendidos utilizados para la creación de una ventana. Si `dwExStyle` es 0, los valores de estilo de plantilla ( `t_dwExStyle`) se devuelven. Si `dwExStyle` es distinto de cero, `dwExStyle` se devuelve.  
  
### <a name="return-value"></a>Valor devuelto  
 Los estilos de ventana extendidos del objeto.  
  
## <a name="see-also"></a>Vea también  
 [Miembros de clase](http://msdn.microsoft.com/en-us/dbe6a147-3f01-4aea-a3fb-fe6ebadc31f8)   
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Descripción de rasgos de las ventanas](../../atl/understanding-window-traits.md)

