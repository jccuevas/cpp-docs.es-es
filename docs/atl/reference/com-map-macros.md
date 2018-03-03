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
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e97db324dc8e130418419ef435e2665c84eb0b64
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
  
 [!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]  
  

  
##  <a name="end_com_map"></a>END_COM_MAP  
 Termina la definición de la asignación de interfaz COM.  
  
```
END_COM_MAP()
```  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)   
 [Funciones globales de mapa COM](../../atl/reference/com-map-global-functions.md)
