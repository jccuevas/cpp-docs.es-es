---
title: Objetos de datos y orígenes de datos (OLE) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data objects [MFC], definition
- data transfer [MFC]
- OLE [MFC], data transfer
- data sources [MFC], definition
- data transfer [MFC], definition
- OLE [MFC], data objects
- OLE [MFC], data sources
ms.assetid: 8f68eed8-0ce8-4489-a4cc-f95554f89090
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 766148494c6b8693f8d9e65f27e157b58d8e8689
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="data-objects-and-data-sources-ole"></a>Objetos de datos y orígenes de datos (OLE)
Cuando se realiza una transferencia de datos, ya sea mediante el Portapapeles o arrastrar y colocar los datos tienen un origen y un destino. Una aplicación proporciona los datos para copiar y otra aplicación lo acepta para pegarlo. Cada parte de la transferencia debe realizar distintas operaciones en los mismos datos para la transferencia sea correcta. La biblioteca (Microsoft Foundation Classes) proporciona dos clases que representan cada parte de esta transferencia:  
  
-   Orígenes de datos (tal como lo implementan `COleDataSource` objetos) que representa el lado de origen de la transferencia de datos. Se crean mediante la aplicación de origen cuando los datos se va a copiar en el Portapapeles, o cuando se proporcionan datos para una operación de arrastrar y colocar.  
  
-   Objetos de datos (tal como lo implementan `COleDataObject` objetos) que representa el lado de destino de la transferencia de datos. Se crean cuando la aplicación de destino tiene datos quitan en él, o cuando se le solicita realizar una operación de pegar desde el Portapapeles.  
  
 Los artículos siguientes explican cómo utilizar objetos de datos y orígenes de datos en las aplicaciones. Esta información se aplica a las aplicaciones de contenedor y servidor, ya que se puede llamar al copiar y pegar datos.  
  
-   [Objetos de datos y orígenes de datos: Creación y destrucción](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [Objetos de datos y orígenes de datos: Manipulación](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## <a name="in-this-section"></a>En esta sección  
 [Arrastrar y colocar](../mfc/drag-and-drop-ole.md)  
  
 [Portapapeles](../mfc/clipboard.md)  
  
## <a name="see-also"></a>Vea también  
 [OLE](../mfc/ole-in-mfc.md)   
 [Clase COleDataObject](../mfc/reference/coledataobject-class.md)   
 [COleDataSource (clase)](../mfc/reference/coledatasource-class.md)
