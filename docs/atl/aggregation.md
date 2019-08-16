---
title: Agregación
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
ms.openlocfilehash: 288af427bd6a8d9baf572dfad8e4a25452694ad9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491981"
---
# <a name="aggregation"></a>Agregación

Hay ocasiones en las que el implementador de un objeto desea aprovechar las ventajas de los servicios ofrecidos por otro objeto precompilado. Además, le gustaría que este segundo objeto apareciera como una parte natural de la primera. COM logra ambos objetivos a través de la contención y la agregación.

La agregación significa que el objeto contenedor (externo) crea el objeto contenido (interno) como parte de su proceso de creación y el exterior expone las interfaces del objeto interno. Un objeto permite ser agregable o no. Si es así, debe seguir ciertas reglas para que la agregación funcione correctamente.

Principalmente, todas `IUnknown` las llamadas a métodos en el objeto contenido deben delegar en el objeto contenedor.

## <a name="see-also"></a>Vea también

[Introducción a COM](../atl/introduction-to-com.md)<br/>
[Reutilizar objetos](/windows/win32/com/reusing-objects)
