---
title: ATL y el subprocesamiento libre serializador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, free threaded marshaler
- free threaded marshaler
- threading [C++], marshaler in ATL
- threading [ATL], free threaded marshaler
- FTM in ATL
ms.assetid: 2db88a13-2217-4ebc-aa7e-432d5da902eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1716985adf65b714a418f20d3873f45c32d368b4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355831"
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL y el contador de referencias de subprocesamiento libre
Página de atributos ATL Simple objeto del asistente incluye una opción que permite a la clase agregar el contador de referencias de subprocesamiento libre (FTM).  
  
 El asistente genera código para crear una instancia del contador de referencias de subprocesamiento libre en `FinalConstruct` y esa instancia en la versión `FinalRelease`. A `COM_INTERFACE_ENTRY_AGGREGATE` macro se agrega automáticamente a la asignación de COM para asegurarse de que `QueryInterface` las solicitudes para [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707) se controlan mediante el contador de referencias de subprocesamiento libre.  
  
 El contador de referencias de subprocesamiento libre permite el acceso directo a las interfaces en el objeto desde cualquier subproceso en el mismo proceso, lo que acelera la llamadas entre apartamentos. Esta opción está pensada para las clases que utilizan el modelo de subprocesamiento Both.  
  
 Cuando se usa esta opción, las clases deben asumir la responsabilidad de la seguridad para subprocesos de sus datos. Además, los objetos que agregan el contador de referencias de subprocesamiento libre y necesitan usar punteros de interfaz obtenidos de otros objetos deben realizar pasos adicionales para asegurarse de que las interfaces se serializan correctamente. Normalmente, esto implica almacenar los punteros de interfaz en la tabla de interfaz global (GIT) y obtener el puntero de la GIT cada vez que se utilice. ATL proporciona la clase [CComGITPtr](../atl/reference/ccomgitptr-class.md) que le ayudarán a utilizar los punteros de interfaz almacenados en la GIT.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)   
 [CoCreateFreeThreadedMarshaler](http://msdn.microsoft.com/library/windows/desktop/ms694500)   
 [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707)   
 [Cuándo se debe utilizar la tabla de interfaz Global](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [Problemas de subprocesamiento de servidor en proceso](http://msdn.microsoft.com/library/windows/desktop/ms687205)

