---
title: Agregación
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
ms.openlocfilehash: d5a09dcd8c289447491ebc7111a77549166a7d00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633423"
---
# <a name="aggregation"></a>Agregación

Hay veces cuando desea que el implementador de un objeto para aprovechar las ventajas de los servicios ofrecidos por otro objeto creado previamente. Además, desea este segundo objeto aparezca como una parte natural de la primera. COM logra ambos objetivos mediante la contención y la agregación.

Agregación significa que el objeto contenedor (externo) crea el objeto de (interno) independiente como parte de su proceso de creación y externo expone las interfaces del objeto interno. Un objeto permite que se pueden agregar o no. Si es así, debe seguir ciertas reglas de agregación para funcionar correctamente.

Principalmente, todos `IUnknown` deben delegar llamadas al método en el objeto contenido en el objeto contenedor.

## <a name="see-also"></a>Vea también

[Introducción a COM](../atl/introduction-to-com.md)<br/>
[Reutilizar objetos](/windows/desktop/com/reusing-objects)

