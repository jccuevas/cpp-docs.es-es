---
title: Interfaces (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: 56d5a010bc28257dce181ee33e0ddf74655ccd3c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319390"
---
# <a name="interfaces-atl"></a>Interfaces (ATL)

Una interfaz es la forma en que un objeto expone su funcionalidad al mundo exterior. En COM, una interfaz es una tabla de punteros (como un C++ vtable) a las funciones implementadas por el objeto. La tabla representa la interfaz y las funciones a las que apunta son los métodos de esa interfaz. Un objeto puede exponer tantas interfaces como elija.

Cada interfaz se basa en la interfaz COM fundamental, [IUnknown](../atl/iunknown.md). Los métodos para `IUnknown` permitir la navegación a otras interfaces expuestas por el objeto.

Además, a cada interfaz se le da un ID de interfaz único (IID). Esta singularidad hace que sea fácil de soportar el control de versiones de la interfaz. Una nueva versión de una interfaz es simplemente una nueva interfaz, con un nuevo IID.

> [!NOTE]
> Los ID para las interfaces COM y OLE estándar están predefinidos.

## <a name="see-also"></a>Consulte también

[Introducción a COM](../atl/introduction-to-com.md)<br/>
[Objetos e interfaces COM](/windows/win32/com/com-objects-and-interfaces)
