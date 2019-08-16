---
title: Interfaces (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: 2373351330982623ffa602fd81bec61d0bc257b2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492138"
---
# <a name="interfaces-atl"></a>Interfaces (ATL)

Una interfaz es la forma en que un objeto expone su funcionalidad al mundo exterior. En COM, una interfaz es una tabla de punteros (como una C++ vtable) a las funciones implementadas por el objeto. La tabla representa la interfaz y las funciones a las que apunta son los métodos de esa interfaz. Un objeto puede exponer tantas interfaces como elija.

Cada interfaz se basa en la interfaz COM fundamental, [IUnknown](../atl/iunknown.md). Los métodos de `IUnknown` permiten la navegación a otras interfaces expuestas por el objeto.

Además, a cada interfaz se le asigna un identificador único de interfaz (IID). Esta unicidad facilita la compatibilidad con el control de versiones de la interfaz. Una nueva versión de una interfaz es simplemente una nueva interfaz, con un nuevo IID.

> [!NOTE]
>  Los IID para las interfaces estándar de COM y OLE están predefinidos.

## <a name="see-also"></a>Vea también

[Introducción a COM](../atl/introduction-to-com.md)<br/>
[Objetos e interfaces COM](/windows/win32/com/com-objects-and-interfaces)
