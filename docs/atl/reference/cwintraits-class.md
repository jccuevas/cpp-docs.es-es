---
title: Clase CWinTraits | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CWinTraits
- ATLWIN/ATL::CWinTraits
- ATLWIN/ATL::CWinTraits::GetWndExStyle
- ATLWIN/ATL::CWinTraits::GetWndStyle
dev_langs:
- C++
helpviewer_keywords:
- CMDIChildWinTraits class
- window styles, default values for ATL
- CWinTraits class
- CFrameWinTraits class
- CControlWinTraits class
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea1eafc6376c44a09d13fb513d41f222048708d9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362513"
---
# <a name="cwintraits-class"></a>Clase CWinTraits
Esta clase proporciona un método para estandarizar los estilos utilizados al crear un objeto de ventana.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
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
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinTraits::GetWndExStyle](#getwndexstyle)|(Estático) Recupera los estilos extendidos para el `CWinTraits` objeto.|  
|[CWinTraits::GetWndStyle](#getwndstyle)|(Estático) Recupera los estilos estándar para la `CWinTraits` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Esto [rasgos de las ventanas](../../atl/understanding-window-traits.md) clase proporciona un método sencillo para estandarizar los estilos utilizados para la creación de un objeto de ventana ATL. Usar una especialización de esta clase como un parámetro de plantilla a [CWindowImpl](../../atl/reference/cwindowimpl-class.md) u otro de clases de ventana de ATL para especificar los estilos predeterminados estándar y extendido usa para instancias de esa clase de ventana.  
  
 Utilice esta plantilla cuando desee proporcionar predeterminado estilos de ventana que se utilizará sólo cuando no hay otros estilos se especifican en la llamada a [CWindowImpl:: Create](../../atl/reference/cwindowimpl-class.md#create).  
  
 ATL proporciona tres especializaciones predefinidas de esta plantilla para combinaciones usadas con frecuencia de estilos de ventana:  
  
 `CControlWinTraits`  
 Diseñado para una ventana de control estándar. Se usan los siguientes estilos estándares: **WS_CHILD**, **WS_VISIBLE**, **WS_CLIPCHILDREN**, y **WS_CLIPSIBLINGS**. No hay ningún estilos extendidos.  
  
 `CFrameWinTraits`  
 Diseñado para una ventana de marco estándar. Los estilos estándares utilizados incluyen: **WS_OVERLAPPEDWINDOW**, **WS_CLIPCHILDREN**, y **WS_CLIPSIBLINGS**. Los estilos extendidos utilizados incluyen: **WS_EX_APPWINDOW** y **WS_EX_WINDOWEDGE**.  
  
 `CMDIChildWinTraits`  
 Diseñado para una ventana secundaria MDI estándar. Los estilos estándares utilizados incluyen: **WS_OVERLAPPEDWINDOW**, **WS_CHILD**, **WS_VISIBLE**, **WS_CLIPCHILDREN**y **WS_CLIPSIBLINGS**. Los estilos extendidos utilizados incluyen: **WS_EX_MDICHILD**.  
  
 Si desea asegurarse de que se han establecido determinados estilos para todas las instancias de la clase de ventana al permitir otros estilos que se establecerá en una base por instancia, utilice [CWinTraitsOR](../../atl/reference/cwintraitsor-class.md) en su lugar.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
  
##  <a name="getwndstyle"></a>  CWinTraits::GetWndStyle  
 Llame a esta función para recuperar los estilos estándar de la `CWinTraits` objeto.  
  
```
static DWORD GetWndStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Estilos estándar que se usan para la creación de una ventana. Si `dwStyle` es 0, los valores de estilo de plantilla ( `t_dwStyle`) se devuelven. Si `dwStyle` es distinto de cero, `dwStyle` se devuelve.  
  
### <a name="return-value"></a>Valor devuelto  
 Los estilos de ventana estándar del objeto.  
  
##  <a name="getwndexstyle"></a>  CWinTraits::GetWndExStyle  
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
 [Información general de clases](../../atl/atl-class-overview.md)   
 [Descripción de rasgos de las ventanas](../../atl/understanding-window-traits.md)
