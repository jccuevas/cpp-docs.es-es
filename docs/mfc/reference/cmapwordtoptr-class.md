---
title: "CMapWordToPtr Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMapWordToPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "16-bit word mapping"
  - "CMapWordToPtr class"
ms.assetid: b204d87f-6427-43e1-93e3-a4b1bb41099f
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CMapWordToPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Admite los mapas de punteros vacíos cerrados por palabras de 16 bits.  
  
## Sintaxis  
  
```  
class CMapWordToPtr : public CObject  
```  
  
## Members  
 Las funciones miembro de `CMapWordToPtr` son similares a las funciones miembro de clases [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md).  Debido a esta similitud, puede utilizar la documentación de referencia de `CMapStringToOb` para las características de la función miembro.  Siempre que aparezca un puntero de `CObject` como un parámetro o valor devuelto de la función, utilice un puntero a `void`.  Siempre que se vea `CString` o un puntero de **const** a `char` como un parámetro o valor devuelto de la función, **word**sustituto.  
  
 `BOOL CMapStringToOb::Lookup( const char* <key>,`  
  
 `CObject*& <rValue> ) const;`  
  
 por ejemplo, convierte a  
  
 `BOOL CMapWordToPtr::Lookup( WORD <key>, void*& <rValue> ) const;`  
  
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
 `CMapWordToPtr` escribe la macro de `IMPLEMENT_DYNAMIC` para admitir el acceso de tipo en tiempo de ejecución y volcar a `CDumpContext` un objeto.  Si necesita un volcado individuales asigne los elementos, debe establecer el nivel de contexto de volcado en 1 o posterior.  
  
 los mapas del Palabra\-a\-puntero pueden no ser serializados.  
  
 Cuando se elimina un objeto de `CMapWordToPtr` , o cuando se quitan los elementos, se quitan las palabras y punteros.  No quitar las entidades a las que hace referencia punteros.  
  
 Para obtener más información sobre `CMapWordToPtr`, vea el artículo [colecciones](../../mfc/collections.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapWordToPtr`  
  
## Requisitos  
 **encabezado:** afxcoll.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)