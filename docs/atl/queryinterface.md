---
title: QueryInterface
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
ms.openlocfilehash: de2762cff3d697261e159336d866a5a7cb10fafa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492005"
---
# <a name="queryinterface"></a>QueryInterface

Aunque hay mecanismos por los que un objeto puede expresar la funcionalidad que proporciona de forma estática (antes de que se cree una instancia), el mecanismo com fundamental es `IUnknown` usar el método denominado [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)).

Cada interfaz se deriva de `IUnknown`, por lo que cada interfaz tiene una `QueryInterface`implementación de. Independientemente de la implementación, este método consulta un objeto utilizando el IID de la interfaz a la que el llamador desea un puntero. Si el objeto admite esa interfaz, `QueryInterface` recupera un puntero a la interfaz, mientras que también llama `AddRef`a. De lo contrario, devuelve el código de error E_NOINTERFACE.

Tenga en cuenta que debe obedecer las reglas de recuento de [referencias](../atl/reference-counting.md) en todo momento. Si llama `Release` a en un puntero de interfaz para reducir el recuento de referencias a cero, no debe volver a usar ese puntero. En ocasiones, puede que necesite obtener una referencia débil a un objeto (es decir, puede que desee obtener un puntero a una de sus interfaces sin incrementar el recuento de referencias), pero no es aceptable hacerlo llamando `QueryInterface` a seguido de. `Release` El puntero Obtenido de este modo no es válido y no debe usarse. Esto se hace más fácil cuando se define [_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces) , por lo que la definición de esta macro es una manera útil de buscar errores de recuento de referencias.

## <a name="see-also"></a>Vea también

[Introducción a COM](../atl/introduction-to-com.md)<br/>
[QueryInterface Desplazarse por un objeto](/windows/win32/com/queryinterface--navigating-in-an-object)
