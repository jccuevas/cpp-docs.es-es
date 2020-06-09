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
ms.openlocfilehash: dfe400dddfecce3e52337f7f449e975dff2ca83e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616217"
---
# <a name="data-objects-and-data-sources-ole"></a>Objetos de datos y orígenes de datos (OLE)

Al realizar una transferencia de datos, ya sea mediante el portapapeles o arrastrando y colocando, los datos tienen un origen y un destino. Una aplicación proporciona los datos para la copia y otra aplicación la acepta para pegarlos. Cada lado de la transferencia debe realizar distintas operaciones en los mismos datos para que la transferencia se realice correctamente. La biblioteca de Microsoft Foundation Class (MFC) proporciona dos clases que representan cada lado de esta transferencia:

- Los orígenes de datos (implementados por `COleDataSource` objetos) representan el lado de origen de la transferencia de datos. Los crea la aplicación de origen cuando se copian los datos en el portapapeles, o cuando se proporcionan datos para una operación de arrastrar y colocar.

- Los objetos de datos (implementados por `COleDataObject` objetos) representan el lado de destino de la transferencia de datos. Se crean cuando la aplicación de destino tiene datos colocados en ella o cuando se le pide que realice una operación de pegar desde el portapapeles.

En los siguientes artículos se explica cómo usar objetos de datos y orígenes de datos en las aplicaciones. Esta información se aplica a las aplicaciones de contenedor y de servidor, ya que se puede llamar a ambas para copiar y pegar datos.

- [Objetos de datos y orígenes de datos: Creación y destrucción](data-objects-and-data-sources-creation-and-destruction.md)

- [Objetos de datos y orígenes de datos: Manipulación](data-objects-and-data-sources-manipulation.md)

## <a name="in-this-section"></a>En esta sección

[Arrastrar y colocar](drag-and-drop-ole.md)

[Portapapeles](clipboard.md)

## <a name="see-also"></a>Consulte también

[OLE](ole-in-mfc.md)<br/>
[COleDataObject (clase)](reference/coledataobject-class.md)<br/>
[COleDataSource (clase)](reference/coledatasource-class.md)
