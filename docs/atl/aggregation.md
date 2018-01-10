---
title: "Agregación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8dbb0332bc7e55464e5b8af9d0b57e236f23dc86
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="aggregation"></a>Agregación
Hay ocasiones al implementador de un objeto desea aprovechar las ventajas de los servicios ofrecidos por otro objeto creada previamente. Además, puede desear que este segundo objeto aparezca como una parte natural de la primera. COM logra ambos de estos objetivos a través de contención y la agregación.  
  
 Agregación significa que el objeto contenedor (externo) crea el objeto de (interno) independiente como parte de su proceso de creación y externo expone las interfaces del objeto interno. Un objeto permite a sí mismos ser o no agregables. Si es así, debe seguir ciertas reglas de agregación para funcionar correctamente.  
  
 Principalmente, todos los **IUnknown** llamadas al método en el objeto contenido deben delegar en el objeto contenedor.  
  
## <a name="see-also"></a>Vea también  
 [Introducción a COM](../atl/introduction-to-com.md)   
 [Reutilización de objetos](http://msdn.microsoft.com/library/windows/desktop/ms678443)

