---
title: Agregación | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4e29fd2c7af893fe6bb548db0a3ec3f956576a37
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767316"
---
# <a name="aggregation"></a>Agregación

Hay veces cuando desea que el implementador de un objeto para aprovechar las ventajas de los servicios ofrecidos por otro objeto creado previamente. Además, desea este segundo objeto aparezca como una parte natural de la primera. COM logra ambos objetivos mediante la contención y la agregación.

Agregación significa que el objeto contenedor (externo) crea el objeto de (interno) independiente como parte de su proceso de creación y externo expone las interfaces del objeto interno. Un objeto permite que se pueden agregar o no. Si es así, debe seguir ciertas reglas de agregación para funcionar correctamente.

Principalmente, todos `IUnknown` deben delegar llamadas al método en el objeto contenido en el objeto contenedor.

## <a name="see-also"></a>Vea también

[Introducción a COM](../atl/introduction-to-com.md)   
[Reutilizar objetos](/windows/desktop/com/reusing-objects)

