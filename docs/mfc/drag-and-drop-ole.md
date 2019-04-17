---
title: Arrastrar y colocar (OLE)
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], drag and drop
- drag and drop [MFC]
- OLE applications [MFC], drag and drop
- File Manager drag and drop support [MFC]
- drag and drop [MFC], about OLE drag and drop
- OLE drag and drop [MFC]
ms.assetid: a4595350-ca06-4400-88a1-f0175c76b77b
ms.openlocfilehash: 98bd58745e56a62bf5700e9b5fe4963a7b584953
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58766812"
---
# <a name="drag-and-drop-ole"></a>Arrastrar y colocar (OLE)

La característica de arrastrar y colocar de OLE es principalmente un acceso directo para copiar y pegar datos. Al usar el Portapapeles para copiar o pegar datos, una serie de pasos es necesaria. Seleccione los datos, haga clic en **cortar** o **copia** desde el **editar** menú, mover al archivo de destino, ventana o aplicación, coloque el cursor en la ubicación deseada y haga clic en **Pegar** desde el **editar** menú.

OLE de arrastrar y colocar es diferente del mecanismo de arrastrar y colocar el Administrador de archivos, que solo se puede controlar los nombres de archivo y está diseñado específicamente para pasar los nombres de archivo a las aplicaciones. OLE de arrastrar y colocar es mucho más general. Permite arrastrar y colocar los datos que podrían colocarse también en el Portapapeles.

Cuando se utiliza OLE de arrastrar y colocar, quitar dos pasos del proceso. Seleccionar los datos de la ventana de código fuente (el "origen de colocación"), arrástrelo hasta el destino deseado (el "destino de colocación") y colóquela al soltar el botón del mouse. La operación elimina la necesidad de los menús y es más rápida que la secuencia de copiar y pegar. El único requisito es que el origen de colocación y el destino de colocación deben estar abierto y al menos parcialmente visible en la pantalla.

Usa OLE de arrastrar y colocar, datos pueden transferirse de una ubicación a otra dentro de un documento, entre distintos documentos o entre aplicaciones. Se puede implementar en un contenedor o una aplicación de servidor y cualquier aplicación puede ser un origen de colocación, un destino de colocación o ambos. Si una aplicación tiene soporte técnico de origen y destino de colocación implementan, arrastrar y colocar está habilitada entre ventanas secundarias, o dentro de una ventana. Esta característica, la aplicación puede quedar mucho más fácil de usar.

Si solo desea usar las capacidades de arrastrar y colocar de OLE, vea [arrastrar y colocar: Personalizar](../mfc/drag-and-drop-customizing.md). Puede usar las técnicas explicadas en este artículo para hacer que las aplicaciones que no son compatibles con OLE quitar orígenes. El artículo [arrastrar y colocar: Implementar un destino de colocación](../mfc/drag-and-drop-implementing-a-drop-target.md) se describe cómo implementar la compatibilidad de destino de OLE y aplicaciones que no son compatibles con OLE. También será útil examinar los ejemplos OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md) y [HIERSVR](../overview/visual-cpp-samples.md).

Si no ha leído el [objetos de datos y orígenes de datos (OLE)](../mfc/data-objects-and-data-sources-ole.md) serie de artículos, es posible que desee hacerlo ahora. Estos artículos explican los aspectos básicos de transferencia de datos y cómo implementarlo en sus aplicaciones.

Para obtener más información acerca de arrastrar y colocar, vea:

- [Arrastrar y colocar: Implementación de un origen de colocación](../mfc/drag-and-drop-implementing-a-drop-source.md)

- [Arrastrar y colocar: Implementar un destino de colocación](../mfc/drag-and-drop-implementing-a-drop-target.md)

- [Arrastrar y colocar: Personalizar](../mfc/drag-and-drop-customizing.md)

## <a name="see-also"></a>Vea también

[OLE](../mfc/ole-in-mfc.md)<br/>
[Objetos de datos y orígenes de datos (OLE)](../mfc/data-objects-and-data-sources-ole.md)
