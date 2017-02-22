---
title: "CRuntimeClass Structure | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRuntimeClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRuntimeClass structure"
  - "dynamic class information"
  - "run-time class, CRuntimeClass structure"
  - "tiempo de ejecución, class information"
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CRuntimeClass Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cada clase derivada de `CObject` es asociado a una estructura de `CRuntimeClass` que puede utilizar para obtener información sobre un objeto o la clase base en tiempo de ejecución.  
  
## Sintaxis  
  
```  
struct CRuntimeClass  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRuntimeClass::CreateObject](../Topic/CRuntimeClass::CreateObject.md)|Crea un objeto en tiempo de ejecución.|  
|[CRuntimeClass::FromName](../Topic/CRuntimeClass::FromName.md)|Crea un objeto en tiempo de ejecución utilizando el nombre de clase familiar.|  
|[CRuntimeClass::IsDerivedFrom](../Topic/CRuntimeClass::IsDerivedFrom.md)|Determina si la clase se deriva de la clase especificada.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRuntimeClass::m\_lpszClassName](../Topic/CRuntimeClass::m_lpszClassName.md)|Nombre de la clase.|  
|[CRuntimeClass::m\_nObjectSize](../Topic/CRuntimeClass::m_nObjectSize.md)|El tamaño del objeto en bytes.|  
|[CRuntimeClass::m\_pBaseClass](../Topic/CRuntimeClass::m_pBaseClass.md)|un puntero a la estructura de `CRuntimeClass` de la clase base.|  
|[CRuntimeClass::m\_pfnCreateObject](../Topic/CRuntimeClass::m_pfnCreateObject.md)|un puntero a la función que crea dinámicamente el objeto.|  
|[CRuntimeClass::m\_pfnGetBaseClass](../Topic/CRuntimeClass::m_pfnGetBaseClass.md)|Devuelve la estructura de `CRuntimeClass` \(sólo disponible cuando está vinculado dinámicamente\).|  
|[CRuntimeClass::m\_wSchema](../Topic/CRuntimeClass::m_wSchema.md)|El número del esquema de la clase.|  
  
## Comentarios  
 `CRuntimeClass` es una estructura y por consiguiente no tiene una clase base.  
  
 La capacidad de determinar el tipo de un objeto en tiempo de ejecución es útil cuando la comprobación de tipo adicional de los argumentos de la función es necesaria, o cuando se debe escribir el código especial basado en la clase de un objeto.  La información de la clase en tiempo de ejecución no se admite directamente en el lenguaje C\+\+.  
  
 `CRuntimeClass` proporciona información sobre el objeto relacionado de C\+\+, como un puntero a `CRuntimeClass` de la clase base y el nombre de clase ASCII de la clase relacionada.  Esta estructura también implementa varias funciones que se pueden utilizar para crear dinámicamente los objetos, especificando el tipo de objeto con un nombre familiarizado, y determinandolo si la clase relacionada es derivada de una clase concreta.  
  
 Para obtener más información sobre cómo utilizar `CRuntimeClass`, vea el artículo [Información de acceso de la clase en tiempo de ejecución](../../mfc/accessing-run-time-class-information.md).  
  
## Jerarquía de herencia  
 `CRuntimeClass`  
  
## Requisitos  
 **encabezado:** afx.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CObject::GetRuntimeClass](../Topic/CObject::GetRuntimeClass.md)   
 [CObject::IsKindOf](../Topic/CObject::IsKindOf.md)   
 [RUNTIME\_CLASS](../Topic/RUNTIME_CLASS.md)   
 [IMPLEMENT\_DYNAMIC](../Topic/IMPLEMENT_DYNAMIC.md)   
 [IMPLEMENT\_DYNCREATE](../Topic/IMPLEMENT_DYNCREATE.md)   
 [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md)