---
title: Clase CWinTraitsOR | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR::GetWndExStyle
- ATLWIN/ATL::CWinTraitsOR::GetWndStyle
dev_langs: C++
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ac6cf07fcd6d3703ffb6b483ba19a2d12520cb0a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cwintraitsor-class"></a>Clase CWinTraitsOR
Esta clase proporciona un método para estandarizar los estilos utilizados al crear un objeto de ventana.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <DWORD t_dwStyle = 0,
          DWORD t_dwExStyle = 0, 
          class TWinTraits = CControlWinTraits>
class CWinTraitsOR
```  
  
#### <a name="parameters"></a>Parámetros  
 `t_dwStyle`  
 Estilos de ventana predeterminados.  
  
 `t_dwExStyle`  
 De forma predeterminada, los estilos de ventana extendidos.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinTraitsOR::GetWndExStyle](#getwndexstyle)|Recupera los estilos extendidos para el `CWinTraitsOR` objeto.|  
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|Recupera los estilos estándar para la `CWinTraitsOR` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Esto [rasgos de las ventanas](../../atl/understanding-window-traits.md) clase proporciona un método sencillo para estandarizar los estilos utilizados para la creación de un objeto de ventana ATL. Usar una especialización de esta clase como un parámetro de plantilla a [CWindowImpl](../../atl/reference/cwindowimpl-class.md) u otro de clases de ventana de ATL para especificar el conjunto mínimo de estilos estándares y extendidos que se utilizará para las instancias de esa clase de ventana.  
  
 Usar una especialización de esta plantilla si desea asegurarse de que ciertos estilos se establecen para todas las instancias de la clase de ventana al permitir otros estilos que se establecerá en forma de cada instancia en la llamada a [CWindowImpl:: Create](../../atl/reference/cwindowimpl-class.md#create).  
  
 Si desea proporcionar predeterminado estilos de ventana que se utilizará sólo cuando no hay otros estilos se especifican en la llamada a `CWindowImpl::Create`, use [CWinTraits](../../atl/reference/cwintraits-class.md) en su lugar.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
  
##  <a name="getwndstyle"></a>CWinTraitsOR::GetWndStyle  
 Llame a esta función para recuperar una combinación (mediante el operador lógico OR) de los estilos estándar de la `CWinTraits` objeto y los estilos predeterminados especificados por `t_dwStyle`.  
  
```
static DWORD GetWndStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Estilos utilizados para la creación de una ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 Una combinación de estilos que se pasan en `dwStyle` y el valor predeterminado que los especificados por `t_dwStyle`, mediante el operador lógico OR.  
  
##  <a name="getwndexstyle"></a>CWinTraitsOR::GetWndExStyle  
 Llame a esta función para recuperar una combinación (mediante el operador lógico OR) de los estilos extendidos de la `CWinTraits` objeto y los estilos predeterminados especificados por `t_dwStyle`.  
  
```
static DWORD GetWndExStyle(DWORD dwExStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwExStyle`  
 Estilos extendidos utilizados para la creación de una ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 Una combinación de los estilos extendidos que se pasan en `dwExStyle` y predeterminados especificados por `t_dwExStyle`, con el operador OR lógico  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)   
 [Descripción de rasgos de las ventanas](../../atl/understanding-window-traits.md)

