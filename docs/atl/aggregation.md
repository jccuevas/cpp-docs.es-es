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
ms.openlocfilehash: 83d19e53b50791255b87cfa73a51761e2cdf5e1f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196150"
---
# <a name="aggregation"></a>Agregación
Hay veces cuando desea que el implementador de un objeto para aprovechar las ventajas de los servicios ofrecidos por otro objeto creado previamente. Además, desea este segundo objeto aparezca como una parte natural de la primera. COM logra ambos objetivos mediante la contención y la agregación.  
  
 Agregación significa que el objeto contenedor (externo) crea el objeto de (interno) independiente como parte de su proceso de creación y externo expone las interfaces del objeto interno. Un objeto permite que se pueden agregar o no. Si es así, debe seguir ciertas reglas de agregación para funcionar correctamente.  
  
 Principalmente, todos `IUnknown` deben delegar llamadas al método en el objeto contenido en el objeto contenedor.  
  
## <a name="see-also"></a>Vea también  
 [Introducción a COM](../atl/introduction-to-com.md)   
 [Reutilizar objetos](/windows/desktop/com/reusing-objects)

