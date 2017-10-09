---
title: Clase _U_MENUorID | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
dev_langs:
- C++
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 0ef6563166c658506a33ffa21da285207fbf5275
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="umenuorid-class"></a>Clase _U_MENUorID
Esta clase proporciona contenedores para **CreateWindow** y **CreateWindowEx**.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class _U_MENUorID
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[_U_MENUorID::_U_MENUorID](#_u_menuorid___u_menuorid)|El constructor.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|Un identificador para un menú.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase de argumento de adaptador permite que cualquier IDs ( **UINT**s) o identificadores de menú ( `HMENU`s) que se pasan a una función sin necesidad de realizar una conversión explícita en la parte del llamador.  
  
 Esta clase está diseñada para implementar contenedores de la API de Windows, especialmente el [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) y [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) funciones, ambos de los cuales aceptan un `HMENU` argumento que puede ser un elemento secundario identificador de ventana ( **UINT**) en lugar de un identificador de menú. Por ejemplo, puede ver esta clase en uso como un parámetro a [CWindowImpl:: Create](cwindowimpl-class.md#create).  

  
 La clase define dos sobrecargas del constructor: uno acepta un **UINT** acepta argumentos y el otro un `HMENU` argumento. El **UINT** argumento solo se convierte en una `HMENU` en el constructor y el resultado almacenado en el miembro de datos único de la clase, [m_hMenu](#_u_menuorid__m_hmenu). El argumento para el `HMENU` constructor se almacena directamente sin realizar ninguna conversión.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
  
##  <a name="_u_menuorid__m_hmenu"></a>_U_MENUorID::m_hMenu  
 La clase contiene el valor pasado a cualquiera de sus constructores como un complemento público `HMENU` miembro de datos.  
  
```
HMENU m_hMenu;
```  
  
##  <a name="_u_menuorid___u_menuorid"></a>_U_MENUorID::_U_MENUorID  
 El **UINT** argumento solo se convierte en una `HMENU` en el constructor y el resultado almacenado en el miembro de datos único de la clase, [m_hMenu](#_u_menuorid__m_hmenu).  
  
```
_U_MENUorID(UINT nID);  
_U_MENUorID(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 Un identificador de ventana secundaria.  
  
 `hMenu`  
 Un identificador de menú.  
  
### <a name="remarks"></a>Comentarios  
 El argumento para el `HMENU` constructor se almacena directamente sin realizar ninguna conversión.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)

