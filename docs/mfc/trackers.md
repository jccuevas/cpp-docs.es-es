---
title: Seguimiento | Documentos de Microsoft
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
- trackers [MFC]
- OLE applications [MFC], trackers
- applications [OLE], trackers
- tracking OLE items [MFC]
- OLE containers [MFC], trackers
- CDC class [MFC], trackers
- CRectTracker class [MFC], implementing trackers
- OLE server applications [MFC], trackers
ms.assetid: dcd09399-6637-4621-80e5-d12670429787
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 29e4d3c556a5f7b6b3aed5daa0285ea6c2c15447
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="trackers"></a>Seguimiento
El [CRectTracker](../mfc/reference/crecttracker-class.md) clase proporciona una interfaz de usuario entre los elementos rectangulares en la aplicación y el usuario mediante una variedad de estilos de presentación. Estos estilos incluyen bordes sólidos, sombreados o guiones; un patrón sombreado que abarca el elemento; y controladores que pueden encontrarse fuera o dentro de un borde de tamaño. Los objetos de seguimiento se utilizan a menudo junto con elementos OLE, es decir, los objetos derivados de `COleClientItem`. Los rectángulos de seguimiento proporcionan indicaciones visuales sobre el estado actual del elemento.  
  
 El ejemplo de MFC OLE [OCLIENT](../visual-cpp-samples.md) muestra una interfaz común con los objetos de seguimiento y elementos de cliente OLE desde el punto de vista de una aplicación de contenedor. Para obtener una demostración de los distintos estilos y la capacidad de un objeto de seguimiento, vea el ejemplo general de MFC [RASTREADOR](../visual-cpp-samples.md).  
  
 Para obtener más información sobre cómo implementar objetos de seguimiento en una aplicación OLE, vea [objetos de seguimiento: implementar objetos de seguimiento en una aplicación OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)  
  
## <a name="see-also"></a>Vea también  
 [OLE](../mfc/ole-in-mfc.md)   
 [COleClientItem (clase)](../mfc/reference/coleclientitem-class.md)
