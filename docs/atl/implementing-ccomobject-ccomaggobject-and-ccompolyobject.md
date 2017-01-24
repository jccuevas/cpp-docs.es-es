---
title: "Implementing CComObject, CComAggObject, and CComPolyObject | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CComPolyObject"
  - "CComAggObject"
  - "CComObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComAggObject class"
  - "CComObject class, implementar"
  - "CComPolyObject class, implementar"
  - "CreateInstance (método)"
ms.assetid: 5aabe938-104d-492e-9c41-9f7fb1c62098
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementing CComObject, CComAggObject, and CComPolyObject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las clases de plantilla [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md), y [CComPolyObject](../atl/reference/ccompolyobject-class.md) son siempre la mayoría de las clases derivadas de la cadena de herencia.  Es su responsabilidad controlar todos los métodos de **IUnknown**: `QueryInterface`, `AddRef`, y **Liberar**.  Además, `CComAggObject` y `CComPolyObject` \(cuando se utiliza para los objetos agregados\) proporcionan el recuento de referencias y la semántica especiales de `QueryInterface` necesarios para el desconocido interno.  
  
 Si `CComObject`, `CComAggObject`, o `CComPolyObject` se usa depende de si no declara una \(o no\) de las macros siguientes:  
  
|Macro|Efecto|  
|-----------|------------|  
|`DECLARE_NOT_AGGREGATABLE`|Siempre utiliza `CComObject`.|  
|`DECLARE_AGGREGATABLE`|Utiliza `CComAggObject` si se agrega el objeto y `CComObject` si no es.  `CComCoClass` contiene esta macro en si no se declara ninguna de las macros de **DECLARE\_\*\_AGGREGATABLE** en la clase, esto será el valor predeterminado.|  
|`DECLARE_ONLY_AGGREGATABLE`|Siempre utiliza `CComAggObject`.  Devuelve un error si el objeto no se agrega.|  
|`DECLARE_POLY_AGGREGATABLE`|ATL crea una instancia de **CComPolyObject\<CYourClass\>** cuando se llama a **IClassFactory::CreateInstance** .  Durante la creación, el valor desconocido externo se comprueba.  si es **NULL**, **IUnknown** se implementa para un objeto nonaggregated.  Si el hecho exterior no se **NULL**, **IUnknown** se implementa para un objeto agregado.|  
  
 La ventaja de utilizar `CComAggObject` y `CComObject` es que la implementación de **IUnknown** está optimizada para la clase de objeto que se está creando.  Por ejemplo, un objeto nonaggregated sólo necesita un recuento de referencia, mientras que un objeto agregado necesita un recuento de referencia para el desconocido interno y un puntero al desconocido externo.  
  
 La ventaja de utilizar `CComPolyObject` es que se evita tener `CComAggObject` y `CComObject` en el módulo para controlar los casos agregado y nonaggregated.  Los controladores de objeto de `CComPolyObject` ambos casos.  Esto significa que sólo una copia de vtable y una copia de las funciones existen en el módulo.  Si el vtable es grande, esto puede reducir considerablemente el tamaño del módulo.  Sin embargo, si el vtable es pequeño, mediante `CComPolyObject` pueden producir un tamaño ligeramente mayor de módulo porque no se optimiza para un objeto agregado o nonaggregated, al igual que `CComAggObject` y `CComObject`.  
  
## Vea también  
 [Fundamentals of ATL COM Objects](../atl/fundamentals-of-atl-com-objects.md)   
 [Aggregation and Class Factory Macros](../atl/reference/aggregation-and-class-factory-macros.md)