---
title: Clase CWinTraitsOR | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CWinTraitsOR
- ATL::CWinTraitsOR
- CWinTraitsOR
dev_langs:
- C++
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
caps.latest.revision: 20
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
ms.openlocfilehash: cd077c7f79c3099d0e825a48233e7a8b269c0d04
ms.lasthandoff: 02/24/2017

---
# <a name="cwintraitsor-class"></a>Clase CWinTraitsOR
Esta clase proporciona un método para estandarizar los estilos utilizados al crear un objeto de ventana.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <DWORD t_dwStyle = 0,
          DWORD t_dwExStyle = 0, 
          class TWinTraits = CControlWinTraits>
class CWinTraitsOR
```  
  
#### <a name="parameters"></a>Parámetros  
 `t_dwStyle`  
 Estilos de ventana predeterminado.  
  
 `t_dwExStyle`  
 De forma predeterminada, los estilos de ventana extendidos.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWinTraitsOR::GetWndExStyle](#getwndexstyle)|Recupera los estilos extendidos para el `CWinTraitsOR` objeto.|  
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|Recupera los estilos estándar para la `CWinTraitsOR` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Esto [rasgos de las ventanas](../../atl/understanding-window-traits.md) clase proporciona un método sencillo de estandarizar los estilos utilizados para la creación de un objeto de ventana ATL. Usar una especialización de esta clase como un parámetro de plantilla a [CWindowImpl](../../atl/reference/cwindowimpl-class.md) u otra de las clases de ventana de ATL para especificar el conjunto mínimo de estilos estándares y extendidos que se utilizará para las instancias de esa clase de ventana.  
  
 Utilice una especialización de esta plantilla si desea asegurarse de que determinados estilos para todas las instancias de la clase de ventana al tiempo que permite a otros estilos que se establecen para cada instancia en la llamada a [CWindowImpl:: Create](../../atl/reference/cwindowimpl-class.md#create).  
  
 Si desea proporcionar predeterminado estilos de ventana que se utilizará sólo cuando no hay otros estilos especificados en la llamada a `CWindowImpl::Create`, utilice [CWinTraits](../../atl/reference/cwintraits-class.md) en su lugar.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
  
##  <a name="a-namegetwndstylea--cwintraitsorgetwndstyle"></a><a name="getwndstyle"></a>CWinTraitsOR::GetWndStyle  
 Llame a esta función para recuperar una combinación (mediante el operador lógico OR) de los estilos estándar de la `CWinTraits` objeto y los estilos predeterminados especificados por `t_dwStyle`.  
  
```
static DWORD GetWndStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Estilos utilizados para la creación de una ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 Una combinación de estilos que se pasan en `dwStyle` y el valor predeterminado que los especificados por `t_dwStyle`, mediante el operador lógico OR.  
  
##  <a name="a-namegetwndexstylea--cwintraitsorgetwndexstyle"></a><a name="getwndexstyle"></a>CWinTraitsOR::GetWndExStyle  
 Llame a esta función para recuperar una combinación (mediante el operador lógico OR) de los estilos extendidos de la `CWinTraits` objeto y los estilos predeterminados especificados por `t_dwStyle`.  
  
```
static DWORD GetWndExStyle(DWORD dwExStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwExStyle`  
 Estilos extendidos utilizados para la creación de una ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 Una combinación de los estilos extendidos que se pasan en `dwExStyle` y predeterminados especificados por `t_dwExStyle`, mediante el operador lógico OR  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Descripción de rasgos de las ventanas](../../atl/understanding-window-traits.md)


