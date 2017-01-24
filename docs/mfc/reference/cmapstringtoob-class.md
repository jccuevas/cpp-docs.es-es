---
title: "CMapStringToOb Class | Microsoft Docs"
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
  - "CMapStringToOb"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMapStringToOb class"
  - "clases de colección, string mapping"
  - "cadenas [C++], class for mapping"
ms.assetid: 09653980-b885-4f3a-8594-0aeb7f94c601
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMapStringToOb Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una clase de colección de diccionarios que asigna los objetos únicos de `CString` a punteros de `CObject` .  
  
## Sintaxis  
  
```  
class CMapStringToOb : public CObject  
```  
  
## Members  
  
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
 Una vez que ha insertado un par de `CString`\- de`CObject*` \(elemento\) en el mapa, puede recuperar o eliminar eficazmente los pares mediante una cadena o un valor de `CString` como clave.  También puede iterar por todos los elementos del mapa.  
  
 Una variable de **POSITION** tipo se utiliza para el acceso alternativo de entrada en todas las variaciones asignadas.  Puede utilizar **POSICIÓN** “recuerda” una entrada y iterarlo a través del mapa.  Crea que esta iteración es secuencial por valor de clave; no es.  La secuencia de elementos recuperados es indeterminado.  
  
 `CMapStringToOb` escribe la macro de `IMPLEMENT_SERIAL` para admitir la serialización y volcar de sus elementos.  Cada elemento es serializado a su vez si un mapa se almacena en un archivo, con el operador sobrecargado de inserción \(**\<\<**\) o con la función miembro de `Serialize` .  
  
 Si necesita un volcado de memoria de diagnóstico de elementos individuales en el mapa \(el valor de `CString` y el contenido de `CObject` \), debe establecer el nivel de contexto de volcado de memoria en 1 o posterior.  
  
 Cuando se elimina un objeto de `CMapStringToOb` , o cuando se quitan los elementos, se quitan los objetos de `CString` y los punteros de `CObject` .  Los objetos hacen referencia a los punteros de `CObject` no se destruyen.  
  
 Derivación de la clase de mapa es similar a la derivación de lista.  Vea el artículo [colecciones](../../mfc/collections.md) para una ilustración de derivación de una clase especial de la lista.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToOb`  
  
## Requisitos  
 **encabezado:** afxcoll.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CMapPtrToPtr Class](../../mfc/reference/cmapptrtoptr-class.md)   
 [CMapPtrToWord Class](../../mfc/reference/cmapptrtoword-class.md)   
 [CMapStringToPtr Class](../../mfc/reference/cmapstringtoptr-class.md)   
 [CMapStringToString Class](../../mfc/reference/cmapstringtostring-class.md)   
 [CMapWordToOb Class](../../mfc/reference/cmapwordtoob-class.md)   
 [CMapWordToPtr Class](../../mfc/reference/cmapwordtoptr-class.md)