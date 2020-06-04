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
ms.openlocfilehash: 94e4961c69e9441d160d72d9b72afcee3677e25f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491910"
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL y el contador de referencias de subprocesamiento libre

La página atributos del Asistente para objetos simples ATL proporciona una opción que permite a la clase agregar el contador de referencias de subprocesamiento libre (FTM).

El asistente genera código para crear una instancia del contador de referencias de subprocesamiento libre `FinalConstruct` en y liberar esa instancia `FinalRelease`en. Se agrega automáticamente una macro COM_INTERFACE_ENTRY_AGGREGATE al mapa com para asegurarse de que `QueryInterface` las solicitudes de [IMarshal](/windows/win32/api/objidlbase/nn-objidlbase-imarshal) se controlan mediante el contador de referencias de subprocesamiento libre.

El contador de referencias de subprocesamiento libre permite el acceso directo a las interfaces del objeto desde cualquier subproceso en el mismo proceso, lo que acelera las llamadas entre apartamentos. Esta opción está pensada para las clases que utilizan el modelo de subprocesos de ambos.

Al utilizar esta opción, las clases deben asumir la responsabilidad de la seguridad para subprocesos de sus datos. Además, los objetos que agregan el serializador de subprocesamiento libre y necesitan usar punteros de interfaz obtenidos de otros objetos deben realizar pasos adicionales para asegurarse de que las referencias de las interfaces son correctas. Normalmente esto implica almacenar los punteros de interfaz en la tabla de interfaz global (GIT) y obtener el puntero de GIT cada vez que se usa. ATL proporciona la clase [CComGITPtr](../atl/reference/ccomgitptr-class.md) para ayudarle a usar punteros de interfaz almacenados en Git.

## <a name="see-also"></a>Vea también

[Conceptos](../atl/active-template-library-atl-concepts.md)<br/>
[CoCreateFreeThreadedMarshaler](/windows/win32/api/combaseapi/nf-combaseapi-cocreatefreethreadedmarshaler)<br/>
[IMarshal](/windows/win32/api/objidlbase/nn-objidlbase-imarshal)<br/>
[Cuándo usar la tabla de interfaz global](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[Problemas de subprocesos de servidor en proceso](/windows/win32/com/in-process-server-threading-issues)
