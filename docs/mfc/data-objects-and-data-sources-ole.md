---
title: Objetos de datos y orígenes de datos (OLE)
ms.date: 11/04/2016
helpviewer_keywords:
- data objects [MFC], definition
- data transfer [MFC]
- OLE [MFC], data transfer
- data sources [MFC], definition
- data transfer [MFC], definition
- OLE [MFC], data objects
- OLE [MFC], data sources
ms.assetid: 8f68eed8-0ce8-4489-a4cc-f95554f89090
ms.openlocfilehash: 485fa5c62aafa4c116a76547238325d2979bfdc4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298274"
---
# <a name="data-objects-and-data-sources-ole"></a>Objetos de datos y orígenes de datos (OLE)

Al realizar una transferencia de datos, ya sea mediante el Portapapeles o arrastrar y colocar, los datos tienen un origen y un destino. Una aplicación proporciona los datos para copiar y la otra aplicación acepta para pegar. Cada parte de la transferencia se debe realizar distintas operaciones en los mismos datos para la transferencia se realice correctamente. La biblioteca Microsoft Foundation Class (MFC) proporciona dos clases que representan cada parte de esta transferencia:

- Orígenes de datos (como se implementa mediante `COleDataSource` objetos) que representa el lado de origen de la transferencia de datos. Se crean mediante la aplicación de origen cuando los datos que se copiarán en el Portapapeles, o cuando se proporcionan datos para una operación de arrastrar y colocar.

- Objetos de datos (como se implementa mediante `COleDataObject` objetos) que representa el lado de destino de la transferencia de datos. Se crean cuando la aplicación de destino tiene datos que se colocan en él, o cuando se solicita para realizar una operación de pegar desde el Portapapeles.

Los siguientes artículos explican cómo usar objetos de datos y orígenes de datos en sus aplicaciones. Esta información se aplica a las aplicaciones de contenedor y servidor, porque ambos se pueden invocar para copiar y pegar datos.

- [Objetos de datos y orígenes de datos: Creación y destrucción](../mfc/data-objects-and-data-sources-creation-and-destruction.md)

- [Objetos de datos y orígenes de datos: Manipulación](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="in-this-section"></a>En esta sección

[Arrastrar y colocar](../mfc/drag-and-drop-ole.md)

[Portapapeles](../mfc/clipboard.md)

## <a name="see-also"></a>Vea también

[OLE](../mfc/ole-in-mfc.md)<br/>
[COleDataObject (clase)](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource (clase)](../mfc/reference/coledatasource-class.md)
