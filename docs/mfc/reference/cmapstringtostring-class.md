---
title: "CMapStringToString Class | Microsoft Docs"
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
  - "CMapStringToString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMapStringToString class"
  - "clases de colección, string mapping"
  - "cadenas [C++], class for mapping"
  - "cadenas [C++], asignar"
ms.assetid: b45794c2-fe6b-4edb-a8ca-faa03b57b4a8
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMapStringToString Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

admite mapas de los objetos de `CString` cerrados por los objetos de `CString` .  
  
## Sintaxis  
  
```  
class CMapStringToString : public CObject  
```  
  
## Members  
 Las funciones miembro de `CMapStringToString` son similares a las funciones miembro de clases [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md).  Debido a esta similitud, puede utilizar la documentación de referencia de `CMapStringToOb` para las características de la función miembro.  Siempre que aparezca un puntero de `CObject` como parámetro de función del valor devuelto o “resultado”, utilice un puntero a `char`.  Siempre que aparezca un puntero de `CObject` como parámetro de la función “entrada”, utilice un puntero a `char`.  
  
 `BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`  
  
 por ejemplo, convierte a  
  
 `BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`  
  
### estructuras públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMapStringToString::CPair](../Topic/CMapStringToString::CPair.md)|Una estructura anidada que contiene un valor de clave y el valor del objeto string asociado.|  
  
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
|[CMapStringToString::PGetFirstAssoc](../Topic/CMapStringToString::PGetFirstAssoc.md)|obtiene un puntero a primer `CString` en el mapa.|  
|[CMapStringToString::PGetNextAssoc](../Topic/CMapStringToString::PGetNextAssoc.md)|Obtiene un puntero a `CString` siguiente para recorrer.|  
|[CMapStringToString::PLookup](../Topic/CMapStringToString::PLookup.md)|Devuelve un puntero a `CString` cuyo valor coincide con el valor especificado.|  
|[CMapStringToOb::RemoveAll](../Topic/CMapStringToOb::RemoveAll.md)|Quita todos los elementos del mapa.|  
|[CMapStringToOb::RemoveKey](../Topic/CMapStringToOb::RemoveKey.md)|Quita un elemento especificado por una clave.|  
|[CMapStringToOb::SetAt](../Topic/CMapStringToOb::SetAt.md)|Inserta un elemento en la asignación; reemplaza un elemento existente si se encuentra una clave coincidente.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMapStringToOb::operator](../Topic/CMapStringToOb::operator.md)|Inserta un elemento en la asignación — sustitución de operador para `SetAt`.|  
  
## Comentarios  
 `CMapStringToString` escribe la macro de `IMPLEMENT_SERIAL` para admitir la serialización y volcar de sus elementos.  Cada elemento es serializado a su vez si un mapa se almacena en un archivo, con el operador sobrecargado de inserción \(**\<\<**\) o con la función miembro de `Serialize` .  
  
 Si necesita un volcado de `CString`individual \(elementos de`CString` , debe establecer el nivel de contexto de volcado en 1 o posterior.  
  
 Cuando se elimina un objeto de `CMapStringToString` , o cuando se quitan los elementos, los objetos de `CString` se quitan según corresponda.  
  
 Para obtener más información sobre `CMapStringToString`, vea el artículo [colecciones](../../mfc/collections.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToString`  
  
## Requisitos  
 **encabezado:** afxcoll.h  
  
## Vea también  
 [El ejemplo de MFC como GET](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)