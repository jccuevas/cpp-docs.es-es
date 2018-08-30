---
title: _U_MENUorID (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9853cbcecd691f0ea16358259c8a0ac7b213433
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211192"
---
# <a name="umenuorid-class"></a>_U_MENUorID (clase)
Esta clase proporciona contenedores para `CreateWindow` y `CreateWindowEx`.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class _U_MENUorID
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[_U_MENUorID::_U_MENUorID](#_u_menuorid___u_menuorid)|El constructor.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|Identificador de un menú.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase de adaptador de argumento permite identificadores (unidades) o identificadores de menú (HMENUs) que se pasará a una función sin necesidad de realizar una conversión explícita por parte del autor de la llamada.  
  
 Esta clase está diseñada para la implementación de contenedores a la API de Windows, especialmente la [CreateWindow](https://msdn.microsoft.com/library/windows/desktop/ms632679) y [CreateWindowEx](https://msdn.microsoft.com/library/windows/desktop/ms632680) funciones, que aceptan un argumento HMENU que puede ser una ventana secundaria identificador (UINT) en lugar de un identificador de menú. Por ejemplo, puede ver esta clase en uso como un parámetro a [CWindowImpl:: Create](cwindowimpl-class.md#create).  

  
 La clase define dos sobrecargas del constructor: uno acepta un argumento UINT y otra que acepta un argumento HMENU. HMENU del constructor y el resultado almacenado en el miembro de datos única de la clase, simplemente se convierte el argumento UINT [m_hMenu](#_u_menuorid__m_hmenu). El argumento del constructor HMENU se almacena directamente sin conversión.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
  
##  <a name="_u_menuorid__m_hmenu"></a>  _U_MENUorID::m_hMenu  
 La clase contiene el valor pasado a cualquiera de sus constructores como un miembro de datos público HMENU.  
  
```
HMENU m_hMenu;
```  
  
##  <a name="_u_menuorid___u_menuorid"></a>  _U_MENUorID::_U_MENUorID  
 HMENU del constructor y el resultado almacenado en el miembro de datos única de la clase, simplemente se convierte el argumento UINT [m_hMenu](#_u_menuorid__m_hmenu).  
  
```
_U_MENUorID(UINT nID);  
_U_MENUorID(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 *nID*  
 Un identificador de ventana secundaria.  
  
 *hMenu*  
 Identificador de menú.  
  
### <a name="remarks"></a>Comentarios  
 El argumento del constructor HMENU se almacena directamente sin conversión.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
