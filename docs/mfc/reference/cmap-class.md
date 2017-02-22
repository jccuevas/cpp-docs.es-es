---
title: "CMap Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMap class"
  - "clases de colección, dictionary mapping"
  - "dictionary mapping class"
ms.assetid: 640a45ab-0993-4def-97ec-42cc78eb10b9
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una clase de colección de diccionarios que asigna las claves únicas en valores.  
  
## Sintaxis  
  
```  
template< class KEY, class ARG_KEY, class VALUE, class ARG_VALUE >class CMap : public CObject  
```  
  
#### Parámetros  
 `KEY`  
 Clase de objeto utilizado como clave al mapa.  
  
 `ARG` *\_* `KEY`  
 tipo de datos utilizado para los argumentos de `KEY` ; normalmente una referencia a `KEY`.  
  
 `VALUE`  
 Clase del objeto en el mapa.  
  
 `ARG` *\_* `VALUE`  
 tipo de datos utilizado para los argumentos de `VALUE` ; normalmente una referencia a `VALUE`.  
  
## Members  
  
### estructuras públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMap::CPair](../Topic/CMap::CPair.md)|Una estructura anidada que contiene un valor de clave y el valor del objeto asociado.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMap::CMap](../Topic/CMap::CMap.md)|Crea una colección que asigna las claves para los valores.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMap::GetCount](../Topic/CMap::GetCount.md)|Devuelve el número de elementos del mapa.|  
|[CMap::GetHashTableSize](../Topic/CMap::GetHashTableSize.md)|Devuelve el número de elementos de la tabla hash.|  
|[CMap::GetNextAssoc](../Topic/CMap::GetNextAssoc.md)|Obtiene el elemento siguiente para recorrer.|  
|[CMap::GetSize](../Topic/CMap::GetSize.md)|Devuelve el número de elementos del mapa.|  
|[CMap::GetStartPosition](../Topic/CMap::GetStartPosition.md)|Devuelve la posición del primer elemento.|  
|[CMap::InitHashTable](../Topic/CMap::InitHashTable.md)|Inicializa la tabla hash y especificar su tamaño.|  
|[CMap::IsEmpty](../Topic/CMap::IsEmpty.md)|Comprueba la condición de vacío\-mapa \(ningún elemento\).|  
|[CMap::Lookup](../Topic/CMap::Lookup.md)|Busca el valor asignado a una clave especificada.|  
|[CMap::PGetFirstAssoc](../Topic/CMap::PGetFirstAssoc.md)|Devuelve un puntero al primer elemento.|  
|[CMap::PGetNextAssoc](../Topic/CMap::PGetNextAssoc.md)|Obtiene un puntero al elemento siguiente para recorrer.|  
|[CMap::PLookup](../Topic/CMap::PLookup.md)|Devuelve un puntero a una clave cuyo valor coincide con el valor especificado.|  
|[CMap::RemoveAll](../Topic/CMap::RemoveAll.md)|Quita todos los elementos del mapa.|  
|[CMap::RemoveKey](../Topic/CMap::RemoveKey.md)|Quita un elemento especificado por una clave.|  
|[CMap::SetAt](../Topic/CMap::SetAt.md)|Inserta un elemento en la asignación; reemplaza un elemento existente si se encuentra una clave coincidente.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMap::operator](../Topic/CMap::operator.md)|Inserta un elemento en la asignación — sustitución de operador para `SetAt`.|  
  
## Comentarios  
 Una vez que ha insertado un par clave\-valor \(elemento\) en el mapa, puede recuperar o eliminar eficazmente los pares con la tecla de acceso.  También puede iterar por todos los elementos del mapa.  
  
 Una variable de **POSICIÓN** tipo se utiliza para el acceso alternativo a entradas.  Puede utilizar **POSICIÓN** “recuerda” una entrada y iterarlo a través del mapa.  Crea que esta iteración es secuencial por valor de clave; no es.  La secuencia de elementos recuperados es indeterminado.  
  
 Algunas funciones miembro de las funciones globales de esta de la clase auxiliar de llamada que se deben personalizar para la mayoría de utilizan la clase de `CMap` .  Vea [aplicaciones auxiliares de la clase de colección](../../mfc/reference/collection-class-helpers.md) en la sección de macros y Globals de `MFC``Reference`.  
  
 `CMap` reemplaza [CObject::Serialize](../Topic/CObject::Serialize.md) para admitir la serialización y volcar de sus elementos.  Si un mapa se almacena en un archivo con `Serialize`, cada elemento asignado es serializado a su vez.  La implementación predeterminada de la función auxiliar de `SerializeElements` realiza una escritura bit a bit.  Para obtener información sobre la serialización de los elementos de colección de puntero derivados de `CObject` u otros tipos definidos por el usuario, vea [Cómo: Crear una colección con seguridad de tipos](../../mfc/how-to-make-a-type-safe-collection.md).  
  
 Si necesita un volcado de diagnóstico de elementos individuales en el mapa \(claves y valores\), debe establecer el nivel de contexto de volcado en 1 o posterior.  
  
 Cuando se elimina un objeto de `CMap` , o cuando se quitan los elementos, se quitan las claves y valores ambas.  
  
 Derivación de la clase de mapa es similar a la derivación de lista.  Vea el artículo [colecciones](../../mfc/collections.md) para una ilustración de derivación de una clase especial de la lista.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMap`  
  
## Requisitos  
 **encabezado:** afxtempl.h  
  
## Vea también  
 [El ejemplo de MFC como GET](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)