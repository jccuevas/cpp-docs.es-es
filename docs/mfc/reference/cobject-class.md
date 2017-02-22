---
title: "CObject Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases base, objetos MFC"
  - "CObject class"
  - "object classes"
  - "objetos [C++], base class for MFC"
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase base principal para la biblioteca Microsoft Foundation Class.  
  
## Sintaxis  
  
```  
class AFX_NOVTABLE CObject  
```  
  
## Miembros  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CObject::CObject](../Topic/CObject::CObject.md)|Constructor predeterminado.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CObject::AssertValid](../Topic/CObject::AssertValid.md)|valida la integridad de este objeto.|  
|[CObject::Dump](../Topic/CObject::Dump.md)|genera un volcado de diagnóstico de este objeto.|  
|[CObject::GetRuntimeClass](../Topic/CObject::GetRuntimeClass.md)|devuelve la estructura de `CRuntimeClass` correspondiente a la esta clase de objeto.|  
|[CObject::IsKindOf](../Topic/CObject::IsKindOf.md)|Prueba la relación de este objeto para una clase determinada.|  
|[CObject::IsSerializable](../Topic/CObject::IsSerializable.md)|Pruebas para ver si este objeto se puede serializar.|  
|[CObject::Serialize](../Topic/CObject::Serialize.md)|Se carga o almacenan un objeto from\/to un archivo.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CObject::operator delete](../Topic/CObject::operator%20delete.md)|operador especial de **cancelación** .|  
|[CObject::operator new](../Topic/CObject::operator%20new.md)|operador especial de **nuevo** .|  
  
## Comentarios  
 Actúa como la raíz no sólo para las clases de biblioteca como `CFile` y `CObList`, sino también para las clases que escribe.  `CObject` proporciona servicios básicos, incluidos  
  
-   Compatibilidad de serialización  
  
-   Información de la clase en tiempo de ejecución  
  
-   Salida de diagnóstico de objeto  
  
-   compatibilidad con las clases de colección  
  
 Observe que `CObject` no admite la herencia múltiple.  Las clases derivadas solo pueden tener una clase base de `CObject` , y que `CObject` debe ser de izquierda en la jerarquía.  Se permite, sin embargo, tener las estructuras y`CObject`no \- clases derivadas en las bifurcaciones derechos de herencia múltiple.  
  
 Realizará ventajas importantes de derivación de `CObject` si utiliza algunas de las macros opcionales en la implementación y las declaraciones de clase.  
  
 Las macros de primer nivel, [DECLARE\_DYNAMIC](../Topic/DECLARE_DYNAMIC.md) y [IMPLEMENT\_DYNAMIC](../Topic/IMPLEMENT_DYNAMIC.md), acceso en tiempo de ejecución de permisos al nombre de clase y su posición en la jerarquía.  esto, a su vez, permite volcar de diagnóstico significativo.  
  
 Las macros de segundo nivel, [DECLARE\_SERIAL](../Topic/DECLARE_SERIAL.md) y [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md), incluyen toda la funcionalidad de las macros de primer nivel, y permiten a un objeto como “serializadas” en un “archivo”.  
  
 Para obtener información sobre la derivación de clases de windows workflow foundation de Microsoft y las clases de C\+\+ en general y utilizar `CObject`, vea [Mediante CObject](../../mfc/using-cobject.md) y [serialización](../../mfc/serialization-in-mfc.md).  
  
## Jerarquía de herencia  
 `CObject`  
  
## Requisitos  
 **encabezado:** afx.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)