---
title: 'Arrastrar y colocar: personalización | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- drag and drop [MFC], implementing in non-OLE applications
- drag and drop [MFC], customizing behavior
- drag and  [MFC], COleDataSource object
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], customizing behavior
ms.assetid: 03369d3e-46bf-4140-b58c-d0c9657cf38a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 59ec5a5a493106750fa7bb8c7ec31b8dbb011070
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344248"
---
# <a name="drag-and-drop-customizing"></a>Arrastrar y colocar: Personalización
La implementación predeterminada de la característica de arrastrar y colocar es suficiente para la mayoría de las aplicaciones. Sin embargo, algunas aplicaciones pueden requerir que se puede cambiar este comportamiento estándar. Este artículo explica los pasos necesarios para cambiar estos valores predeterminados. Además, puede usar esta técnica para establecer las aplicaciones que no son compatibles con documentos compuestos como orígenes de colocación.  
  
 Si desea personalizar el comportamiento de arrastrar y colocar OLE estándar, o si tiene una aplicación no son compatibles con OLE, debe crear un `COleDataSource` objeto que contiene los datos. Cuando el usuario inicia una operación de arrastrar y colocar, el código debe llamar a la `DoDragDrop` función de este objeto en lugar de otras clases que admiten operaciones de arrastrar y colocar.  
  
 Si lo desea, puede crear un `COleDropSource` objeto para controlar la colocación e invalidar algunas de sus funciones, según el tipo de comportamiento que desea cambiar. A continuación, se pasa este objeto de origen de colocación a `COleDataSource::DoDragDrop` para cambiar el comportamiento predeterminado de estas funciones. Estas opciones ofrecen un gran flexibilidad en el modo admiten operaciones de arrastrar y colocar en la aplicación. Para obtener más información acerca de los orígenes de datos, vea el artículo [objetos de datos y orígenes de datos (OLE)](../mfc/data-objects-and-data-sources-ole.md).  
  
 Puede invalidar las siguientes funciones para personalizar las operaciones de arrastrar y colocar:  
  
|invalidación|Para personalizar|  
|--------------|------------------|  
|`OnBeginDrag`|¿Cómo se inicia el arrastre después de llamar a `DoDragDrop`.|  
|`GiveFeedback`|Información visual, como la apariencia del cursor, para colocar distintos resultados.|  
|`QueryContinueDrag`|La finalización de una operación de arrastrar y colocar. Esta función le permite comprobar estados clave de modificador durante la operación de arrastre.|  
  
## <a name="see-also"></a>Vea también  
 [Arrastrar y colocar (OLE)](../mfc/drag-and-drop-ole.md)   
 [Clase COleDropSource](../mfc/reference/coledropsource-class.md)   
 [COleDataSource (clase)](../mfc/reference/coledatasource-class.md)
