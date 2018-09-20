---
title: 'Arrastrar y colocar: personalización | Microsoft Docs'
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
ms.openlocfilehash: 7dd7e88d6843ec3d95538e482c6c05a3d853f4d1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390775"
---
# <a name="drag-and-drop-customizing"></a>Arrastrar y colocar: Personalización

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
