---
title: Agregación | Documentos de Microsoft
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
ms.openlocfilehash: 760a595274ba7a1901138cc0cceceddf97122725
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32353968"
---
# <a name="aggregation"></a>Agregación
Hay ocasiones al implementador de un objeto desea aprovechar las ventajas de los servicios ofrecidos por otro objeto creada previamente. Además, puede desear que este segundo objeto aparezca como una parte natural de la primera. COM logra ambos de estos objetivos a través de contención y la agregación.  
  
 Agregación significa que el objeto contenedor (externo) crea el objeto de (interno) independiente como parte de su proceso de creación y externo expone las interfaces del objeto interno. Un objeto permite a sí mismos ser o no agregables. Si es así, debe seguir ciertas reglas de agregación para funcionar correctamente.  
  
 Principalmente, todos los **IUnknown** llamadas al método en el objeto contenido deben delegar en el objeto contenedor.  
  
## <a name="see-also"></a>Vea también  
 [Introducción a COM](../atl/introduction-to-com.md)   
 [Reutilización de objetos](http://msdn.microsoft.com/library/windows/desktop/ms678443)

