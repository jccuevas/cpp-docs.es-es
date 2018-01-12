---
title: "Colección de ATL y las clases de enumerador | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8b172c0d3a6f453ec0d5f7b5bb3584ebf2f5140e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="atl-collection-and-enumerator-classes"></a>Colección de ATL y las clases de enumerador
ATL proporciona las siguientes clases para ayudar a implementar colecciones y enumeradores.  
  
|Clase|Descripción|  
|-----------|-----------------|  
|[ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)|Implementación de la interfaz de colección|  
|[IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)|Implementación de la interfaz de enumerador (asume datos almacenados en un contenedor compatible de biblioteca estándar de C++)|  
|[CComEnumImpl](../atl/reference/ccomenumimpl-class.md)|Implementación de la interfaz de enumerador (asume datos almacenados en una matriz)|  
|[CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)|Implementación de objeto enumerador (usa `IEnumOnSTLImpl`)|  
|[CComEnum](../atl/reference/ccomenum-class.md)|Implementación de objeto enumerador (usa `CComEnumImpl`)|  
|[_Copy](../atl/atl-copy-policy-classes.md)|Clase de directiva de copia|  
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|Clase de directiva de copia|  
|[CAdapt](../atl/reference/cadapt-class.md)|Clase de adaptador (oculta **operador &** permitir `CComPtr`, `CComQIPtr`, y `CComBSTR` que se almacenará en contenedores de la biblioteca estándar de C++)|  
  
## <a name="see-also"></a>Vea también  
 [Colecciones y enumeradores](../atl/atl-collections-and-enumerators.md)

