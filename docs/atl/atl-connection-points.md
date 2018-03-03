---
title: "Puntos de conexión ATL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- connections, connection points
- ATL, connection points
- connection points [C++], about connection points
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2063bd35627fd86c0cab82e4e50e5e8a126ddfa7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="atl-connection-points"></a>Puntos de conexión en ATL
Un objeto conectable es aquel que acepta interfaces de salida. Una interfaz de salida permite que el objeto se comunique con un cliente. Para cada interfaz de salida, el objeto conectable expone un punto de conexión. Cada interfaz de salida es implementada por un cliente en un objeto denominado receptor.  
  
 ![Puntos de conexión](../atl/media/vc2zw31.gif "vc2zw31")  
  
 Cada punto de conexión admite la [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318) interfaz. El objeto conectable expone sus puntos de conexión al cliente a través de la [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857) interfaz.  
  
## <a name="in-this-section"></a>En esta sección  
 [Clases de puntos de conexión ATL](../atl/atl-connection-point-classes.md)  
 Describe brevemente las clases ATL compatibles con puntos de conexión.  
  
 [Agregar puntos de conexión a un objeto](../atl/adding-connection-points-to-an-object.md)  
 Describe los pasos utilizados para agregar puntos de conexión a un objeto.  
  
 [Ejemplo de puntos de conexión ATL](../atl/atl-connection-point-example.md)  
 Proporciona un ejemplo de cómo declarar un punto de conexión.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Proporciona vínculos a temas sobre cómo programar utilizando Active Template Library.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)

