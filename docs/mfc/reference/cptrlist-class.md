---
title: Clase CPtrList | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPtrList
dev_langs:
- C++
helpviewer_keywords:
- lists, generic
- CPtrList class [MFC]
- generic lists
ms.assetid: 4139a09c-4338-4f42-9eea-51336120b43c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d7e69c8c0d80fea2720ea436bf0bff796ae57a60
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cptrlist-class"></a>Clase CPtrList
Admite listas de punteros void.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CPtrList : public CObject  
```  
  
## <a name="members"></a>Miembros  
 Las funciones miembro de `CPtrList` son similares a las funciones miembro de clase [CObList](../../mfc/reference/coblist-class.md). Debido a esta similitud, puede utilizar la documentación de referencia de `CObList` para obtener información específica de la función miembro. Siempre que vea un puntero `CObject` como un parámetro o un valor devuelto de función, utilice un puntero a `void`.  
  
 `CObject*& CObList::GetHead() const;`  
  
 por ejemplo, se traduce en  
  
 `void*& CPtrList::GetHead() const;`  
  
## <a name="remarks"></a>Comentarios  
 `CPtrList` incorpora la macro `IMPLEMENT_DYNAMIC` para admitir el acceso a tipos en tiempo de ejecución y el volcado en un objeto `CDumpContext`. Si se necesita un volcado de elementos de lista de punteros individuales, se debe establecer la profundidad del contexto de volcado en 1 o un valor superior.  
  
 Las listas de punteros no se pueden serializar.  
  
 Cuando se elimina un objeto `CPtrList`, o cuando se quitan sus elementos, solo se quitan los punteros, no las entidades a las que hacen referencia.  
  
 Para obtener más información sobre el uso de `CPtrList`, vea el artículo [colecciones](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CPtrList`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcoll.h  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CObList (clase)](../../mfc/reference/coblist-class.md)
