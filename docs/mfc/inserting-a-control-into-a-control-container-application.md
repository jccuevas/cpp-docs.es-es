---
title: 'Contenedores de controles ActiveX: Insertar un control en una aplicación de contenedor de controles'
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], inserting controls
- ActiveX controls [MFC], adding to projects
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
ms.openlocfilehash: 1d2fc82628b3bcf842a6efb1d36ab9e8389fc0ba
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618492"
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>Contenedores de controles ActiveX: Insertar un control en una aplicación de contenedor de controles

Para poder tener acceso a un control ActiveX desde una aplicación contenedora de controles ActiveX, debe agregar el control ActiveX a la aplicación contenedora mediante el cuadro de diálogo [Insertar control ActiveX](../windows/insert-activex-control-dialog-box.md) .

Para agregar un control ActiveX al proyecto de contenedor de controles ActiveX, vea [ver y agregar controles ActiveX a un cuadro de diálogo](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).

Una vez agregado el control, debe agregar una variable miembro (del tipo de control ActiveX) a la clase de cuadro de diálogo. Para obtener más información sobre este procedimiento, vea [Agregar una variable de miembro](../ide/adding-a-member-variable-visual-cpp.md).

Una vez agregada la variable miembro, se genera automáticamente una clase, denominada clase contenedora, que se agrega al proyecto. Esta clase se usa como una interfaz entre el contenedor de control y el control incrustado.

## <a name="see-also"></a>Consulte también

[Contenedores de controles ActiveX](activex-control-containers.md)
