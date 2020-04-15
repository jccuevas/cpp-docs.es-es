---
title: Implementación de una interfaz dual (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
ms.openlocfilehash: a85597adad045bee3edb5cc3ed63c72a22fa08fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319467"
---
# <a name="implementing-a-dual-interface"></a>Implementación de una interfaz dual

Puede implementar una interfaz dual mediante la clase [IDispatchImpl,](../atl/reference/idispatchimpl-class.md) que proporciona una implementación predeterminada de los `IDispatch` métodos en una interfaz dual. Para obtener más información, consulta [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

Para utilizar esta clase:

- Defina la interfaz dual en una biblioteca de tipos.

- Derive la clase de `IDispatchImpl` una especialización de (pasar información sobre la interfaz y la biblioteca de tipos como argumentos de plantilla).

- Agregue una entrada (o entradas) al mapa COM `QueryInterface`para exponer la interfaz dual a través de .

- Implemente la parte vtable de la interfaz de la clase.

- Asegúrese de que la biblioteca de tipos que contiene la definición de interfaz está disponible para los objetos en tiempo de ejecución.

## <a name="atl-simple-object-wizard"></a>Asistente para objetos simples ATL

Si desea crear una nueva interfaz y una nueva clase para implementarla, puede usar el cuadro de [diálogo Agregar clase de ATL](../ide/add-class-dialog-box.md)y, a continuación, el Asistente para [objetos simples de ATL](../atl/reference/atl-simple-object-wizard.md).

## <a name="implement-interface-wizard"></a>Asistente para implementar interfaces

Si tiene una interfaz existente, puede usar el [Asistente para implementar interfaz](../atl/reference/adding-a-new-interface-in-an-atl-project.md) para agregar la clase base necesaria, las entradas de mapa COM y las implementaciones de método de esqueleto a una clase existente.

> [!NOTE]
> Es posible que deba ajustar la clase base generada para que los números de `IDispatchImpl` versión principal y secundaria de la biblioteca de tipos se pasen como argumentos de plantilla a la clase base. El Asistente para implementar interfaz no comprueba el número de versión de la biblioteca de tipos.

## <a name="implementing-idispatch"></a>Implementación de IDispatch

Puede utilizar `IDispatchImpl` una clase base para proporcionar una implementación de una interfaz dispinterface simplemente especificando la entrada adecuada en el mapa COM (mediante la macro [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) o [COM_INTERFACE_ENTRY_IID)](reference/com-interface-entry-macros.md#com_interface_entry_iid) siempre que tenga una biblioteca de tipos que describa una interfaz dual correspondiente. Es bastante común implementar `IDispatch` la interfaz de esta manera, por ejemplo. El Asistente para objetos simples de ATL y `IDispatch` el Asistente para implementar interfaz suponen que tiene la intención de implementar de esta manera, por lo que agregarán la entrada adecuada al mapa.

> [!NOTE]
> ATL ofrece las clases [IDispEventImpl](../atl/reference/idispeventimpl-class.md) e [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) para ayudarle a implementar dispinterfaces sin necesidad de una biblioteca de tipos que contenga la definición de una interfaz dual compatible.

## <a name="see-also"></a>Consulte también

[Interfaces duales y ATL](../atl/dual-interfaces-and-atl.md)
