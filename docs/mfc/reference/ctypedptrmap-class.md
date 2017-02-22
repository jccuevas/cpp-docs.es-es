---
title: "CTypedPtrMap Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CTypedPtrMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTypedPtrMap class"
  - "mapas"
  - "pointer maps"
  - "template classes, CTypedPtrMap class"
  - "type-safe collections"
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CTypedPtrMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona un “contenedor seguro” para los objetos de las clases `CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`, y `CMapStringToPtr`de puntero\-mapa.  
  
## Sintaxis  
  
```  
template< class BASE_CLASS, class KEY, class VALUE >  
class CTypedPtrMap : public BASE_CLASS  
```  
  
#### Parámetros  
 `BASE_CLASS`  
 Clase base del tipo de clase del mapa del puntero; debe ser una clase de mapa de puntero \(`CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`, o `CMapStringToPtr`\).  
  
 `KEY`  
 Clase de objeto utilizado como clave al mapa.  
  
 `VALUE`  
 Clase del objeto en el mapa.  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTypedPtrMap::GetNextAssoc](../Topic/CTypedPtrMap::GetNextAssoc.md)|Obtiene el elemento siguiente para recorrer.|  
|[CTypedPtrMap::Lookup](../Topic/CTypedPtrMap::Lookup.md)|devuelve `KEY` basado en `VALUE`.|  
|[CTypedPtrMap::RemoveKey](../Topic/CTypedPtrMap::RemoveKey.md)|Quita un elemento especificado por una clave.|  
|[CTypedPtrMap::SetAt](../Topic/CTypedPtrMap::SetAt.md)|Inserta un elemento en la asignación; reemplaza un elemento existente si se encuentra una clave coincidente.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTypedPtrMap::operator](../Topic/CTypedPtrMap::operator.md)|Inserta un elemento en la asignación.|  
  
## Comentarios  
 Cuando se utiliza `CTypedPtrMap`, ayuda a facilitar la comprobación de tipos de C\+\+ eliminan los errores producidos por los tipos de puntero no coincidentes.  
  
 Dado que todas las funciones de `CTypedPtrMap` inline, el uso de esta plantilla no afecta significativamente el tamaño o la velocidad del código.  
  
 Para obtener más información sobre cómo utilizar `CTypedPtrMap`, vea los artículos [colecciones](../../mfc/collections.md) y [Clases basadas en plantillas](../../mfc/template-based-classes.md).  
  
## Jerarquía de herencia  
 `BASE_CLASS`  
  
 `CTypedPtrMap`  
  
## Requisitos  
 **encabezado:** afxtempl.h  
  
## Vea también  
 [El ejemplo de MFC como GET](../../top/visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CMapPtrToPtr Class](../../mfc/reference/cmapptrtoptr-class.md)   
 [CMapPtrToWord Class](../../mfc/reference/cmapptrtoword-class.md)   
 [CMapWordToPtr Class](../../mfc/reference/cmapwordtoptr-class.md)   
 [CMapStringToPtr Class](../../mfc/reference/cmapstringtoptr-class.md)