---
title: Implementar CComObject, CComAggObject y CComPolyObject | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CComPolyObject
- CComAggObject
- CComObject
dev_langs: C++
helpviewer_keywords:
- CComPolyObject class, implementing
- CreateInstance method
- CComAggObject class
- CComObject class, implementing
ms.assetid: 5aabe938-104d-492e-9c41-9f7fb1c62098
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bb74d68bb8974f820ac09a0c56930d835a3fe7f3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="implementing-ccomobject-ccomaggobject-and-ccompolyobject"></a>Implementar CComObject, CComAggObject y CComPolyObject
Las clases de plantilla [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md), y [CComPolyObject](../atl/reference/ccompolyobject-class.md) siempre son las clases más derivadas en la cadena de herencia. Es su responsabilidad para controlar todos los métodos en **IUnknown**: `QueryInterface`, `AddRef`, y **versión**. Además, `CComAggObject` y `CComPolyObject` (cuando se usa para los objetos agregados) proporciona el recuento de referencias especiales y `QueryInterface` semántica necesaria para el objeto desconocido interno.  
  
 Si `CComObject`, `CComAggObject`, o `CComPolyObject` se usa depende de si se declaran una (o ninguna) de las macros siguientes:  
  
|Macro|Efecto|  
|-----------|------------|  
|`DECLARE_NOT_AGGREGATABLE`|Siempre usa `CComObject`.|  
|`DECLARE_AGGREGATABLE`|Usa `CComAggObject` si el objeto es agregado y `CComObject` si no lo está. `CComCoClass`contiene esta macro por lo que si ninguno de los **DECLARE_\*_AGGREGATABLE** macros se declaran en la clase, será el valor predeterminado.|  
|`DECLARE_ONLY_AGGREGATABLE`|Siempre usa `CComAggObject`. Devuelve un error si no se agrega el objeto.|  
|`DECLARE_POLY_AGGREGATABLE`|ATL crea una instancia de **CComPolyObject\<CSuClase >** cuando **IClassFactory:: CreateInstance** se llama. Durante la creación, se comprueba el valor del objeto desconocido externo. Si es **NULL**, **IUnknown** se implementa para un objeto no agregado. Si no se encuentra el desconocido externo **NULL**, **IUnknown** se implementa para un objeto agregado.|  
  
 La ventaja de usar `CComAggObject` y `CComObject` es que la implementación de **IUnknown** está optimizado para el tipo de objeto que se va a crear. Por ejemplo, un objeto no agregado sólo necesita un recuento de referencias, mientras que un objeto agregado necesita tanto un recuento de referencias para el objeto desconocido interno como un puntero para el desconocido externo.  
  
 La ventaja de usar `CComPolyObject` es evitar tener ambos `CComAggObject` y `CComObject` en su módulo para controlar los casos agregados y no agregados. Una sola `CComPolyObject` objeto controla ambos casos. Esto significa que existen solo una copia de la tabla vtable y una copia de las funciones del módulo. Si su tabla vtable es grande, esto puede reducir considerablemente el tamaño del módulo. Sin embargo, si su tabla vtable es pequeña, usando `CComPolyObject` puede dar lugar a un tamaño de módulo ligeramente mayor porque no está optimizado para un objeto agregado o no agregado, como son `CComAggObject` y `CComObject`.  
  
## <a name="see-also"></a>Vea también  
 [Aspectos básicos de los objetos ATL COM](../atl/fundamentals-of-atl-com-objects.md)   
 [Macros de agregación y generador de clases](../atl/reference/aggregation-and-class-factory-macros.md)

