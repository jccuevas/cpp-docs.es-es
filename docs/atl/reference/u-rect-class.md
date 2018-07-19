---
title: _U_RECT (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_U_RECT
- _U_RECT
- ATL._U_RECT
dev_langs:
- C++
helpviewer_keywords:
- U_RECT class
- _U_RECT class
ms.assetid: 5f880a2d-09cf-4327-bf32-a3519c4dcd63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ebb76d2f373862b39f2a3742481e14523a7a94b
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882226"
---
# <a name="urect-class"></a>_U_RECT (clase)
Esta clase de adaptador de argumento permite `RECT` punteros o referencias a pasarse a una función que se implementa en términos de punteros.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class _U_RECT
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[_U_RECT::_U_RECT](#_u_rect___u_rect)|El constructor.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[_U_RECT::m_lpRect](#_u_rect__m_lprect)|Puntero a un `RECT`.|  
  
## <a name="remarks"></a>Comentarios  
 La clase define dos sobrecargas del constructor: uno acepta un **RECT &** argumento y la otra acepta un `LPRECT` argumento. El primer constructor almacena la dirección del argumento de referencia en el miembro de datos única de la clase, [m_lpRect](#_u_rect__m_lprect). El argumento del constructor de puntero se almacena directamente sin conversión.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
  
##  <a name="_u_rect__m_lprect"></a>  _U_RECT::m_lpRect  
 La clase contiene el valor pasado a cualquiera de sus constructores como pública `LPRECT` miembro de datos.  
  
```
LPRECT m_lpRect;
```  
  
##  <a name="_u_rect___u_rect"></a>  _U_RECT::_U_RECT  
 La dirección del argumento de referencia se almacena en el miembro de datos única de la clase, [m_lpRect](#_u_rect__m_lprect).  
  
```
_U_RECT(RECT& rc);  
_U_RECT(LPRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 *rc*  
 Un `RECT` referencia.  
  
 *lpRect*  
 Un `RECT` puntero.  
  
### <a name="remarks"></a>Comentarios  
 El argumento del constructor de puntero se almacena directamente sin conversión.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
