---
title: Colección de ATL y clases de enumerador
ms.date: 11/04/2016
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
ms.openlocfilehash: a0d7483cc142377ec4de903e27f23056a9e8dd8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495312"
---
# <a name="atl-collection-and-enumerator-classes"></a>Colección de ATL y clases de enumerador

ATL proporciona las siguientes clases para ayudarle a implementar colecciones y enumeradores.

|Clase|Descripción|
|-----------|-----------------|
|[ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)|Implementación de la interfaz de colección|
|[IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)|Implementación de la interfaz de enumerador (asume datos almacenados en un contenedor de la biblioteca estándar de C++ compatible)|
|[CComEnumImpl](../atl/reference/ccomenumimpl-class.md)|Implementación de la interfaz de enumerador (asume datos almacenados en una matriz)|
|[CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)|Implementación de objeto enumerador (usa `IEnumOnSTLImpl`)|
|[CComEnum](../atl/reference/ccomenum-class.md)|Implementación de objeto enumerador (usa `CComEnumImpl`)|
|[_Copiar](../atl/atl-copy-policy-classes.md)|Clase de directiva de copia|
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|Clase de directiva de copia|
|[CAdapt](../atl/reference/cadapt-class.md)|Clase de adaptador (oculta **operador &** permitiendo `CComPtr`, `CComQIPtr`, y `CComBSTR` se almacenen en contenedores de la biblioteca estándar de C++)|

## <a name="see-also"></a>Vea también

[Las colecciones y enumeradores](../atl/atl-collections-and-enumerators.md)

