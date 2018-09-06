---
title: Implementar una interfaz Dual (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a362ba60b1601e2b291201e10ac49cf9c0ec1ef
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765988"
---
# <a name="implementing-a-dual-interface"></a>Implementar una interfaz Dual

Puede implementar una interfaz dual con la [IDispatchImpl](../atl/reference/idispatchimpl-class.md) (clase), que proporciona una implementación predeterminada de la `IDispatch` métodos en una interfaz dual. Para obtener más información, consulte [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

Para usar esta clase:

- Definir la interfaz dual en una biblioteca de tipos.

- Derive la clase de una especialización de `IDispatchImpl` (pasar información sobre la biblioteca de interfaz y el tipo como los argumentos de plantilla).

- Agregar una entrada (o entradas) al mapa COM para exponer la interfaz dual a través de `QueryInterface`.

- Implemente la parte vtable de la interfaz en su clase.

- Asegúrese de que la biblioteca de tipos que contiene la definición de interfaz está disponible para los objetos en tiempo de ejecución.

## <a name="atl-simple-object-wizard"></a>Asistente para objetos simples ATL

Si desea crear una nueva interfaz y una nueva clase para su implementación, puede usar el [cuadro de diálogo Agregar clase de ATL](../ide/add-class-dialog-box.md)y, a continuación, el [ATL Simple Object Wizard](../atl/reference/atl-simple-object-wizard.md).

## <a name="implement-interface-wizard"></a>Asistente para implementar interfaces

Si tiene una interfaz existente, puede usar el [Asistente para implementar interfaces](../atl/reference/adding-a-new-interface-in-an-atl-project.md) para agregar la clase base necesaria, entradas de mapa COM y las implementaciones de método de esqueleto a una clase existente.

> [!NOTE]
>  Es posible que deba ajustar la clase base generada de forma que los números de versión principal y secundaria de la biblioteca de tipos se pasan como argumentos de plantilla para su `IDispatchImpl` clase base. El Asistente para implementar interfaces no comprueba el número de versión de la biblioteca de tipos.

## <a name="implementing-idispatch"></a>Implementación de IDispatch

Puede usar un `IDispatchImpl` basar la clase para proporcionar una implementación de una interfaz dispinterface simplemente especificando la entrada apropiada en el mapa COM (mediante el [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) o [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid) macro) siempre que tenga una biblioteca de tipos que describe una interfaz dual correspondiente. Es bastante habitual para implementar el `IDispatch` de la interfaz de este modo, por ejemplo. El Asistente para objetos simples de ATL y el Asistente para implementar interfaces ambos suponen que pretenden implementar `IDispatch` de esta manera, por lo que agregará la entrada correspondiente a la asignación.

> [!NOTE]
>  ATL ofrece el [IDispEventImpl](../atl/reference/idispeventimpl-class.md) y [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) clases que le ayudarán a implementar interfaces dispinterface sin necesidad de una biblioteca de tipos que contiene la definición de una interfaz dual compatible.

## <a name="see-also"></a>Vea también

[Interfaces duales y ATL](../atl/dual-interfaces-and-atl.md)

