---
title: 'Arrastrar y colocar: Personalizar'
ms.date: 11/04/2016
helpviewer_keywords:
- drag and drop [MFC], implementing in non-OLE applications
- drag and drop [MFC], customizing behavior
- drag and  [MFC], COleDataSource object
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], customizing behavior
ms.assetid: 03369d3e-46bf-4140-b58c-d0c9657cf38a
ms.openlocfilehash: b4749f8d45c962f8b9217e4c6367538d3e6a3608
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405955"
---
# <a name="drag-and-drop-customizing"></a>Arrastrar y colocar: Personalizar

La implementación predeterminada de la característica de arrastrar y colocar es suficiente para la mayoría de las aplicaciones. Sin embargo, algunas aplicaciones pueden requerir que se puede cambiar este comportamiento estándar. En este artículo se explica los pasos necesarios para cambiar estos valores predeterminados. Además, puede usar esta técnica para establecer las aplicaciones que no son compatibles con documentos compuestos como orígenes de colocación.

Si desea personalizar el comportamiento de arrastrar y colocar OLE estándar o tiene una aplicación que no son compatibles con OLE, debe crear un `COleDataSource` objeto para contener los datos. Cuando el usuario comienza una operación de arrastrar y colocar, el código debe llamar a la `DoDragDrop` función de este objeto en lugar de desde otras clases que admiten operaciones de arrastrar y colocar.

Opcionalmente, puede crear un `COleDropSource` objeto para controlar la colocación y reemplazar algunas de sus funciones según el tipo de comportamiento que desea cambiar. Este objeto de origen de colocación, a continuación, se pasa a `COleDataSource::DoDragDrop` para cambiar el comportamiento predeterminado de estas funciones. Estas opciones ofrecen un gran flexibilidad en cómo admitir operaciones de arrastrar y colocar en la aplicación. Para obtener más información acerca de los orígenes de datos, vea el artículo [objetos de datos y orígenes de datos (OLE)](../mfc/data-objects-and-data-sources-ole.md).

Puede invalidar las siguientes funciones para personalizar las operaciones de arrastrar y colocar:

|invalidar|Para personalizar|
|--------------|------------------|
|`OnBeginDrag`|¿Cómo se inicia el arrastre después de llamar a `DoDragDrop`.|
|`GiveFeedback`|Comentarios visuales, como la apariencia del cursor, para colocar distintos resultados.|
|`QueryContinueDrag`|La terminación de una operación de arrastrar y colocar. Esta función permite comprobar estados clave de modificador durante la operación de arrastre.|

## <a name="see-also"></a>Vea también

[Arrastrar y colocar (OLE)](../mfc/drag-and-drop-ole.md)<br/>
[COleDropSource (clase)](../mfc/reference/coledropsource-class.md)<br/>
[COleDataSource (clase)](../mfc/reference/coledatasource-class.md)
