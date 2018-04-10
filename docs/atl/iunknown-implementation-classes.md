---
title: Clases de implementación de IUnknown (ATL) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- vc.atl.Iunknown
dev_langs:
- C++
helpviewer_keywords:
- IUnknown implementation classes
ms.assetid: 47b69bb5-69d8-4a9c-84a8-329bdde2bb3f
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 53d5363f6b11904e31ea0e9c6f452b2c8fa7e000
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="iunknown-implementation-classes"></a>Clases de implementación de IUnknown
Las clases siguientes implementan **IUnknown** y otros métodos relacionados:  
  
-   [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) administra el recuento de objetos agregados y referencias. Permite especificar un modelo de subprocesos.  
  
-   [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) administra el recuento de objetos agregados y referencias. Usa el valor predeterminado modelo del servidor de subprocesos.  
  
-   [CComAggObject](../atl/reference/ccomaggobject-class.md) implementa **IUnknown** para un objeto agregado.  
  
-   [CComObject](../atl/reference/ccomobject-class.md) implementa **IUnknown** para un objeto no agregado.  
  
-   [CComPolyObject](../atl/reference/ccompolyobject-class.md) implementa **IUnknown** para los objetos agregados y no agregados. Usar `CComPolyObject` evita tener ambos `CComAggObject` y `CComObject` en el módulo. Una sola `CComPolyObject` objeto administra los casos agregados y no agregados.  
  
-   [CComObjectNoLock](../atl/reference/ccomobjectnolock-class.md) implementa **IUnknown** para un objeto, sin modificar el número de bloqueos de módulo.  
  
-   [CComTearOffObject](../atl/reference/ccomtearoffobject-class.md) implementa **IUnknown** para una interfaz desplazable.  
  
-   [CComCachedTearOffObject](../atl/reference/ccomcachedtearoffobject-class.md) implementa **IUnknown** para una interfaz desplazable "en caché".  
  
-   [CComContainedObject](../atl/reference/ccomcontainedobject-class.md) implementa **IUnknown** para el objeto interno de una agregación o una interfaz desplazable.  
  
-   [CComObjectGlobal](../atl/reference/ccomobjectglobal-class.md) administra un recuento de referencias en el módulo para asegurarse de su objeto no se eliminará.  
  
-   [CComObjectStack](../atl/reference/ccomobjectstack-class.md) crea un objeto COM temporal, con una implementación básica de **IUnknown**.  
  
## <a name="related-articles"></a>Artículos relacionados  
 [Aspectos básicos de los objetos ATL COM](../atl/fundamentals-of-atl-com-objects.md)  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../atl/atl-class-overview.md)   
 [Agregación y Macros de fábrica de clase](../atl/reference/aggregation-and-class-factory-macros.md)   
 [Macros de mapa COM](../atl/reference/com-map-macros.md)   
 [Funciones globales de mapa COM](../atl/reference/com-map-global-functions.md)

