---
title: 'Contenedores de controles ActiveX: Ver y modificar propiedades de control'
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], viewing and modifying
- ActiveX control containers [MFC], viewing and modifying properties
- resource editors, viewing and modifying ActiveX controls
- ActiveX controls [MFC], properties
- controls [MFC], properties
ms.assetid: 14ce5152-742b-4e0d-a9ab-c7b456e32918
ms.openlocfilehash: 1d42820efd06c2ae52f5d1b22b0bdfb6335c4a89
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907806"
---
# <a name="activex-control-containers-viewing-and-modifying-control-properties"></a>Contenedores de controles ActiveX: Ver y modificar propiedades de control

Al insertar un control ActiveX en un proyecto, resulta útil ver y cambiar las propiedades que admite el control ActiveX. En este artículo se describe cómo usar el editor C++ de recursos visual para hacerlo.

Si la aplicación contenedora de controles ActiveX usa controles incrustados, puede ver y modificar las propiedades del control mientras se encuentra en el editor de recursos. También puede usar el editor de recursos para establecer los valores de propiedad durante el tiempo de diseño. A continuación, el editor de recursos guarda automáticamente estos valores en el archivo de recursos del proyecto. Cualquier instancia del control tendrá sus propiedades inicializadas en estos valores.

En este procedimiento se supone que ha insertado un control en el proyecto. Para obtener más información [, vea contenedores de controles ActiveX: Insertar un control en una aplicación](../mfc/inserting-a-control-into-a-control-container-application.md)contenedora de controles.

El primer paso para ver las propiedades del control es agregar una instancia del control a la plantilla de cuadro de diálogo del proyecto.

### <a name="to-view-the-properties-of-a-control"></a>Para ver las propiedades de un control

1. En Vista de recursos, abra la carpeta del **cuadro de diálogo** .

1. Abra la plantilla de cuadro de diálogo principal.

1. Inserte un control ActiveX mediante el cuadro de diálogo **Insertar control ActiveX** . Para obtener más información, vea [ver y agregar controles ActiveX a un cuadro de diálogo](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).

1. Seleccione el control ActiveX en el cuadro de diálogo.

1. En la ventana **propiedades** , haga clic en el botón **propiedades** .

Utilice el cuadro de diálogo **propiedades** para modificar y probar las nuevas propiedades inmediatamente.

## <a name="see-also"></a>Vea también

[Contenedores de controles ActiveX](../mfc/activex-control-containers.md)
