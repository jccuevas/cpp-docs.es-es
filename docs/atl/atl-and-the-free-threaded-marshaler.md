---
title: ATL y el contador de referencias de subprocesamiento libre
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, free threaded marshaler
- free threaded marshaler
- threading [C++], marshaler in ATL
- threading [ATL], free threaded marshaler
- FTM in ATL
ms.assetid: 2db88a13-2217-4ebc-aa7e-432d5da902eb
ms.openlocfilehash: ddea5a74dbd40d097398d04c0b2bc274df5ec972
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300003"
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL y el contador de referencias de subprocesamiento libre

Página de atributos ATL Simple objeto del asistente proporciona una opción que permite que la clase agregar el contador de referencias de subproceso libre (FTM).

El asistente genera código para crear una instancia del contador de referencias de subprocesos libres en `FinalConstruct` y liberar esa instancia en `FinalRelease`. Se agrega automáticamente una macro COM_INTERFACE_ENTRY_AGGREGATE al mapa COM para asegurarse de que `QueryInterface` las solicitudes de [IMarshal](/windows/desktop/api/objidlbase/nn-objidlbase-imarshal) se controlan mediante el contador de referencias de subproceso libre.

El contador de referencias de subproceso libre permite el acceso directo a las interfaces en el objeto desde cualquier subproceso en el mismo proceso, lo que acelera las llamadas entre apartamentos. Esta opción está diseñada para las clases que usan el modelo de subprocesamiento Both.

Cuando se usa esta opción, las clases deben asumir la responsabilidad de la seguridad para subprocesos de sus datos. Además, los objetos que agregan el contador de referencias de subproceso libre y necesitan utilizar punteros de interfaz obtenidos de otros objetos deben realizar pasos adicionales para asegurarse de que las interfaces se serializan correctamente. Normalmente, esto implica almacenar los punteros de interfaz en la tabla de interfaz global (GIT) y obtener el puntero de la GIT cada vez que se utiliza. ATL proporciona la clase [CComGITPtr](../atl/reference/ccomgitptr-class.md) le ayudarán a usar punteros de interfaz almacenados en la GIT.

## <a name="see-also"></a>Vea también

[Conceptos](../atl/active-template-library-atl-concepts.md)<br/>
[CoCreateFreeThreadedMarshaler](/windows/desktop/api/combaseapi/nf-combaseapi-cocreatefreethreadedmarshaler)<br/>
[IMarshal](/windows/desktop/api/objidlbase/nn-objidlbase-imarshal)<br/>
[Cuándo usar la tabla de interfaz Global](/windows/desktop/com/when-to-use-the-global-interface-table)<br/>
[Problemas de subprocesamiento de servidor en proceso](/windows/desktop/com/in-process-server-threading-issues)
