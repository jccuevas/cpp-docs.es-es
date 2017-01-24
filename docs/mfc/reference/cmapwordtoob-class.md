---
title: "CMapWordToOb Class | Microsoft Docs"
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
  - "CMapWordToOb"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "16-bit word mapping"
  - "CMapWordToOb class"
ms.assetid: 9c9bcd76-456f-4cf9-b03c-dd28b49d5e4f
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMapWordToOb Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Admite mapas de punteros de `CObject` cerrados por palabras de 16 bits.  
  
## Sintaxis  
  
```  
class CMapWordToOb : public CObject  
```  
  
## Members  
 Las funciones miembro de `CMapWordToOb` son similares a las funciones miembro de clases [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md).  Debido a esta similitud, puede utilizar la documentación de referencia de `CMapStringToOb` para las características de la función miembro.  Siempre que se vea `CString` o un puntero de **const** a `char` como un parámetro o valor devuelto de la función, **word**sustituto.  
  
 `BOOL CMapStringToOb::Lookup( const char* <key>,`  
  
 `CObject*& <rValue> ) const;`  
  
 por ejemplo, convierte a  
  
 `BOOL CMapWordToOb::Lookup( WORD <key>, CObject*& <rValue> ) const;`  
  
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
 `CMapWordToOb` escribe la macro de `IMPLEMENT_SERIAL` para admitir la serialización y volcar de sus elementos.  Cada elemento es serializado a su vez si un mapa se almacena en un archivo, con el operador sobrecargado de inserción \(**\<\<**\) o con la función miembro de `Serialize` .  
  
 Si necesita un volcado de **word**individual \(elementos de`CObject` , debe establecer el nivel de contexto de volcado en 1 o posterior.  
  
 Cuando se elimina un objeto de `CMapWordToOb` , o cuando se quitan los elementos, se quitan los punteros de `CObject` .  Los objetos hacen referencia a los punteros de `CObject` no se destruyen.  
  
 Para obtener más información sobre `CMapWordToOb`, vea el artículo [colecciones](../../mfc/collections.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapWordToOb`  
  
## Requisitos  
 **encabezado:** afxcoll.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)