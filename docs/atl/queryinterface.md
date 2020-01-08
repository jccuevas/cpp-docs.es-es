---
title: QueryInterface
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
ms.openlocfilehash: 37bb7a8c7fef963f340704561e24e33cc36707f3
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298641"
---
# <a name="queryinterface"></a>QueryInterface

Aunque hay mecanismos por los que un objeto puede expresar la funcionalidad que proporciona de forma estática (antes de que se cree una instancia), el mecanismo COM fundamental es usar el método de `IUnknown` denominado [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)).

Cada interfaz se deriva de `IUnknown`, por lo que cada interfaz tiene una implementación de `QueryInterface`. Independientemente de la implementación, este método consulta un objeto utilizando el IID de la interfaz a la que el llamador desea un puntero. Si el objeto admite esa interfaz, `QueryInterface` recupera un puntero a la interfaz, mientras que también llama a `AddRef`. De lo contrario, devuelve el código de error E_NOINTERFACE.

Tenga en cuenta que debe obedecer las reglas de [recuento de referencias](../atl/reference-counting.md) en todo momento. Si llama a `Release` en un puntero de interfaz para reducir el recuento de referencias a cero, no debe volver a usar ese puntero. En ocasiones, puede que necesite obtener una referencia débil a un objeto (es decir, puede que desee obtener un puntero a una de sus interfaces sin incrementar el recuento de referencias), pero no es aceptable hacerlo llamando a `QueryInterface` seguido de `Release`. El puntero Obtenido de este modo no es válido y no debe usarse. Esto se hace más fácil cuando se define [_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces) , por lo que la definición de esta macro es una manera útil de buscar errores de recuento de referencias.

## <a name="see-also"></a>Vea también

[Introducción a COM](../atl/introduction-to-com.md)<br/>
[QueryInterface: desplazarse por un objeto](/windows/win32/com/queryinterface--navigating-in-an-object)
