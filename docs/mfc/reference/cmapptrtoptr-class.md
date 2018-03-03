---
title: Clase CMapPtrToPtr | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CMapStringToOb [MFC], CMapStringToOb
- CMapStringToOb [MFC], GetCount
- CMapStringToOb [MFC], GetHashTableSize
- CMapStringToOb [MFC], GetNextAssoc
- CMapStringToOb [MFC], GetSize
- CMapStringToOb [MFC], GetStartPosition
- CMapStringToOb [MFC], HashKey
- CMapStringToOb [MFC], InitHashTable
- CMapStringToOb [MFC], IsEmpty
- CMapStringToOb [MFC], Lookup
- CMapStringToOb [MFC], LookupKey
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: 23cbbaec-9d64-48f2-92ae-5e24fa64b926
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b7482e2824874cbe0e1126e49979f9dfd18ba57e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cmapptrtoptr-class"></a>Clase CMapPtrToPtr
Admite mapas de punteros void con clave de punteros void.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMapPtrToPtr : public CObject  
```  
  
## <a name="members"></a>Miembros  
 Las funciones miembro de `CMapPtrToPtr` son similares a las funciones miembro de clase [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Debido a esta similitud, puede utilizar la documentación de referencia de `CMapStringToOb` para obtener información específica de la función miembro. Siempre que vea un puntero `CObject` como un parámetro o un valor devuelto de función, utilice un puntero a `void`. Siempre que vea un `CString` o un **const** puntero a `char` como un parámetro de función o un valor devuelto, utilice un puntero a `void`.  
  
 `BOOL CMapStringToOb::Lookup( const char* <key>,`  
  
 `CObject*& <rValue> ) const;`  
  
 por ejemplo, se traduce en  
  
 `BOOL CMapPtrToPtr::Lookup( void* <key>, void*& <rValue> ) const;`  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMapStringToOb::CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMapStringToOb::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Devuelve el número de elementos de esta asignación.|  
|[CMapStringToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Determina el número actual de elementos de la tabla hash.|  
|[CMapStringToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Obtiene el elemento siguiente para efectuar una iteración.|  
|[CMapStringToOb::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Devuelve el número de elementos de esta asignación.|  
|[CMapStringToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Devuelve la posición del primer elemento.|  
|[CMapStringToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Calcula el valor hash de una clave especificada.|  
|[CMapStringToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicializa la tabla hash.|  
|[CMapStringToOb::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Comprueba si la condición de mapa está vacío (no hay elementos).|  
|[CMapStringToOb::Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Busca un puntero void en función de la clave de puntero void. El valor del puntero, no la entidad que señala, se utiliza para la comparación de claves.|  
|[CMapStringToOb::LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Devuelve una referencia a la clave asociada con el valor de clave especificado.|  
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Quita todos los elementos de esta asignación.|  
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Quita un elemento especificado por una clave.|  
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Inserta un elemento en la asignación; reemplaza un elemento existente si se encuentra una clave coincidente.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[[] CMapStringToOb::operator](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Inserta un elemento en el mapa: sustitución de operador para `SetAt`.|  
  
## <a name="remarks"></a>Comentarios  
 `CMapPtrToPtr` incorpora la macro `IMPLEMENT_DYNAMIC` para admitir el acceso a tipos en tiempo de ejecución y el volcado en un objeto `CDumpContext`. Si se necesita un volcado de elementos de mapa individuales (valores de puntero), debe establecer la profundidad del contexto de volcado en 1 o mayor.  
  
 Puntero al puntero mapas no se pueden serializar.  
  
 Cuando se elimina un objeto `CMapPtrToPtr`, o cuando se quitan sus elementos, solo se quitan los punteros, no las entidades a las que hacen referencia.  
  
 Para obtener más información sobre `CMapPtrToPtr`, vea el artículo [colecciones](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapPtrToPtr`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcoll.h  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



