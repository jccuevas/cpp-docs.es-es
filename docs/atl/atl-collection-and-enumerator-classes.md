---
title: Colección de ATL y las clases de enumerador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a47525bb21b896b0fef8393cab66142ed40311ea
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354451"
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

