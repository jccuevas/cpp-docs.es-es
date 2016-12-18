---
title: "CMapPtrToPtr Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMapPtrToPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMapPtrToPtr class"
  - "clases de colección, pointer mapping"
  - "pointer mapping class"
ms.assetid: 23cbbaec-9d64-48f2-92ae-5e24fa64b926
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMapPtrToPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Admite los mapas de punteros vacíos cerrado por los punteros vacíos.  
  
## Sintaxis  
  
```  
class CMapPtrToPtr : public CObject  
```  
  
## Members  
 Las funciones miembro de `CMapPtrToPtr` son similares a las funciones miembro de clases [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md).  Debido a esta similitud, puede utilizar la documentación de referencia de `CMapStringToOb` para las características de la función miembro.  Siempre que aparezca un puntero de `CObject` como un parámetro o valor devuelto de la función, utilice un puntero a `void`.  Siempre que se vea `CString` o un puntero de **const** a `char` como un parámetro o valor devuelto de la función, utilice un puntero a `void`.  
  
 `BOOL CMapStringToOb::Lookup( const char* <key>,`  
  
 `CObject*& <rValue> ) const;`  
  
 por ejemplo, convierte a  
  
 `BOOL CMapPtrToPtr::Lookup( void* <key>, void*& <rValue> ) const;`  
  
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
 `CMapPtrToPtr` escribe la macro de `IMPLEMENT_DYNAMIC` para admitir el acceso de tipo en tiempo de ejecución y volcar a `CDumpContext` un objeto.  Si necesita un volcado de memoria individuales asigne los elementos \(valores de puntero\), debe establecer el nivel de contexto de volcado de memoria en 1 o posterior.  
  
 Los mapas del Puntero\-a\- puntero no pueden ser serializados.  
  
 Cuando se elimina un objeto de `CMapPtrToPtr` , o cuando se quitan los elementos, solo se quitan los punteros, no las entidades que hacen referencia.  
  
 Para obtener más información sobre `CMapPtrToPtr`, vea el artículo [colecciones](../../mfc/collections.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapPtrToPtr`  
  
## Requisitos  
 **encabezado:** afxcoll.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)