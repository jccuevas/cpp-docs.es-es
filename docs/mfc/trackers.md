---
title: Seguimiento
ms.date: 11/04/2016
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
ms.openlocfilehash: 6dffb5b4326d08daf59098e1888169c2353dafe2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262719"
---
# <a name="trackers"></a>Seguimiento

El [CRectTracker](../mfc/reference/crecttracker-class.md) clase proporciona una interfaz de usuario entre los elementos rectangulares en la aplicación y el usuario mediante una variedad de estilos de presentación. Estos estilos incluyen los bordes, sombreados, continua o discontinuos; un patrón de sombreado que cubre el elemento; y controladores que pueden encontrarse fuera o dentro de un borde de tamaño. Herramientas de seguimiento a menudo se usan junto con los elementos OLE, es decir, los objetos derivados de `COleClientItem`. Los rectángulos de seguimiento proporcionan indicaciones visuales sobre el estado actual del elemento.

El ejemplo OLE de MFC [OCLIENT](../visual-cpp-samples.md) muestra una interfaz común con herramientas de seguimiento y elementos de cliente OLE desde el punto de vista de una aplicación contenedora. Para ver una demostración de los distintos estilos y las capacidades de un objeto de seguimiento, vea el ejemplo general de MFC [TRACKER](../visual-cpp-samples.md).

Para obtener más información sobre cómo implementar objetos de seguimiento en una aplicación OLE, vea [objetos de seguimiento: Implementar el seguimiento en una aplicación OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)

## <a name="see-also"></a>Vea también

[OLE](../mfc/ole-in-mfc.md)<br/>
[COleClientItem (clase)](../mfc/reference/coleclientitem-class.md)
