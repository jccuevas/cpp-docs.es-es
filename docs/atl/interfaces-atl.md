---
title: Interfaces (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: 5416fb8a99420f0f6c84318753ee3399ccf5db2a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250319"
---
# <a name="interfaces-atl"></a>Interfaces (ATL)

Una interfaz es la manera en que un objeto expone su funcionalidad al mundo exterior. En COM, una interfaz es una tabla de punteros (como una vtable de C++) a funciones implementadas por el objeto. La tabla representa la interfaz y las funciones a la que señala son los métodos de esa interfaz. Un objeto puede exponer tantas interfaces como elija.

Cada interfaz se basa en la interfaz COM fundamental, [IUnknown](../atl/iunknown.md). Los métodos de `IUnknown` permiten la navegación a otras interfaces expuestas por el objeto.

Además, cada interfaz tiene una única identificador (IID) de interfaz. Esta singularidad facilita la compatibilidad con las versiones de la interfaz. Una nueva versión de una interfaz es simplemente una nueva interfaz con un nuevo IID.

> [!NOTE]
>  IID para las interfaces COM y OLE estándares están predefinidos.

## <a name="see-also"></a>Vea también

[Introducción a COM](../atl/introduction-to-com.md)<br/>
[Interfaces y objetos COM.](/windows/desktop/com/com-objects-and-interfaces)
