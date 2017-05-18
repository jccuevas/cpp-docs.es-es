---
title: Macros de mapa COM | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
caps.latest.revision: 16
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
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 1c8e73fc4d6cab2e9052e74d68bddbb5796ebfa8
ms.contentlocale: es-es
ms.lasthandoff: 03/31/2017

---
# <a name="com-map-macros"></a>Macros de mapa COM
Estas macros definen los mapas de interfaz COM.  
  
|||  
|-|-|  
|[BEGIN_COM_MAP](#begin_com_map)|Marca el principio de las entradas del mapa de interfaz COM.|  
|[END_COM_MAP](#end_com_map)|Marca el final de las entradas del mapa de interfaz COM.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
   
##  <a name="begin_com_map"></a>BEGIN_COM_MAP  
 La asignación COM no es el mecanismo que expone interfaces en un objeto a un cliente a través de `QueryInterface`.  
  
```
BEGIN_COM_MAP(x)
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] El nombre del objeto de clase en que expone interfaces.  
  
### <a name="remarks"></a>Comentarios  
 [CComObjectRootEx:: InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) sólo devuelve los punteros de interfaces en el mapa COM. Iniciar la asignación de interfaz con el `BEGIN_COM_MAP` macro, agregue entradas para cada una de las interfaces con la [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) macro o una de sus variantes y complete el mapa con la [END_COM_MAP](#end_com_map) macro.  

  
### <a name="example"></a>Ejemplo  
 Desde la biblioteca ATL [BUSCAPERSONAS](../../visual-cpp-samples.md) ejemplo:  
  
 [!code-cpp[NVC_ATL_COM N.º 1](../../atl/codesnippet/cpp/com-map-macros_1.h)]  
  

  
##  <a name="end_com_map"></a>END_COM_MAP  
 Termina la definición de la asignación de interfaz COM.  
  
```
END_COM_MAP()
```  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)   
 [Funciones globales de mapa COM](../../atl/reference/com-map-global-functions.md)

