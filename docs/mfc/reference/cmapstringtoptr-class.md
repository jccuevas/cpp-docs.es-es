---
title: "CMapStringToPtr Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMapStringToPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMapStringToPtr class"
  - "clases de colección, string mapping"
  - "cadenas [C++], class for mapping"
ms.assetid: 1ac11143-eb0a-4511-a662-2df0d1d9005b
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CMapStringToPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Admite los mapas de punteros vacíos cerrados por los objetos de `CString` .  
  
## Sintaxis  
  
```  
class CMapStringToPtr : public CObject  
```  
  
## Members  
 Las funciones miembro de `CMapStringToPtr` son similares a las funciones miembro de clases [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md).  Debido a esta similitud, puede utilizar la documentación de referencia de `CMapStringToOb` para las características de la función miembro.  Siempre que aparezca un puntero de `CObject` como un parámetro o valor devuelto de la función, utilice un puntero a `void`.  
  
 `BOOL CMapStringToOb::Lookup( const char* <key>,`  
  
 `CObject*& <rValue> ) const;`  
  
 por ejemplo, convierte a  
  
 `BOOL CMapStringToPtr::Lookup( LPCTSTR <key>, void*& <rValue> )`  
  
 `const;`  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMapStringToOb::CMapStringToOb](../Topic/CMapStringToOb::CMapStringToOb.md)|Constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMapStringToOb::GetCount](../Topic/CMapStringToOb::GetCount.md)|Devuelve el número de elementos del mapa.|  
|[CMapStringToOb::GetHashTableSize](../Topic/CMapStringToOb::GetHashTableSize.md)|Determina el número actual de elementos de la tabla hash.|  
|[CMapStringToOb::GetNextAssoc](../Topic/CMapStringToOb::GetNextAssoc.md)|Obtiene el elemento siguiente para recorrer.|  
|[CMapStringToOb::GetSize](../Topic/CMapStringToOb::GetSize.md)|Devuelve el número de elementos del mapa.|  
|[CMapStringToOb::GetStartPosition](../Topic/CMapStringToOb::GetStartPosition.md)|Devuelve la posición del primer elemento.|  
|[CMapStringToOb::HashKey](../Topic/CMapStringToOb::HashKey.md)|Calcula el valor hash de una clave especificada.|  
|[CMapStringToOb::InitHashTable](../Topic/CMapStringToOb::InitHashTable.md)|Inicializa la tabla hash.|  
|[CMapStringToOb::IsEmpty](../Topic/CMapStringToOb::IsEmpty.md)|Comprueba la condición de vacío\-mapa \(ningún elemento\).|  
|[CMapStringToOb::Lookup](../Topic/CMapStringToOb::Lookup.md)|Busca un puntero void basándose en la clave del puntero vacía.  El valor del puntero, no la entidad que seleccione, se utiliza para la comparación clave.|  
|[CMapStringToOb::LookupKey](../Topic/CMapStringToOb::LookupKey.md)|Devuelve una referencia a la clave asociada al valor de clave especificado.|  
|[CMapStringToOb::RemoveAll](../Topic/CMapStringToOb::RemoveAll.md)|Quita todos los elementos del mapa.|  
|[CMapStringToOb::RemoveKey](../Topic/CMapStringToOb::RemoveKey.md)|Quita un elemento especificado por una clave.|  
|[CMapStringToOb::SetAt](../Topic/CMapStringToOb::SetAt.md)|Inserta un elemento en la asignación; reemplaza un elemento existente si se encuentra una clave coincidente.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMapStringToOb::operator](../Topic/CMapStringToOb::operator.md)|Inserta un elemento en la asignación — sustitución de operador para `SetAt`.|  
  
## Comentarios  
 `CMapStringToPtr` escribe la macro de `IMPLEMENT_DYNAMIC` para admitir el acceso de tipo en tiempo de ejecución y volcar a `CDumpContext` un objeto.  Si necesita un volcado individuales asigne los elementos, debe establecer el nivel de contexto de volcado en 1 o posterior.  
  
 Los mapas del Cadena\-a\- puntero no pueden ser serializados.  
  
 Cuando se elimina un objeto de `CMapStringToPtr` , o cuando se quitan los elementos, se quitan los objetos de clave de `CString` y palabras.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToPtr`  
  
## Requisitos  
 **encabezado:** afxcoll.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)