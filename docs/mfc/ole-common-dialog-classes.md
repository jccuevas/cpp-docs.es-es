---
title: Clases de cuadros de diálogo comunes OLE
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- dialog classes [MFC], OLE
- OLE common dialog classes [MFC]
- common dialog classes [MFC]
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
ms.openlocfilehash: 1854d19c540f5e3e64b47786f465a05213eced86
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617789"
---
# <a name="ole-common-dialog-classes"></a>Clases de cuadros de diálogo comunes OLE

Estas clases controlan las tareas comunes de OLE implementando una serie de cuadros de diálogo estándar de OLE. También proporcionan una interfaz de usuario coherente para la funcionalidad de OLE.

[COleDialog](reference/coledialog-class.md)<br/>
Lo usa el marco de trabajo para contener implementaciones comunes para todos los cuadros de diálogo de OLE. Todas las clases de cuadro de diálogo de la categoría interfaz de usuario se derivan de esta clase base. `COleDialog`no se puede usar directamente.

[COleInsertDialog](reference/coleinsertdialog-class.md)<br/>
Muestra el cuadro de diálogo Insertar objeto, la interfaz de usuario estándar para insertar nuevos elementos vinculados OLE o incrustados.

[COlePasteSpecialDialog](reference/colepastespecialdialog-class.md)<br/>
Muestra el cuadro de diálogo Pegar especial, la interfaz de usuario estándar para implementar el comando Editar pegado especial.

[COleLinksDialog](reference/colelinksdialog-class.md)<br/>
Muestra el cuadro de diálogo Editar vínculos, la interfaz de usuario estándar para modificar información sobre los elementos vinculados.

[COleChangeIconDialog](reference/colechangeicondialog-class.md)<br/>
Muestra el cuadro de diálogo Cambiar icono, la interfaz de usuario estándar para cambiar el icono asociado a un elemento OLE incrustado o vinculado.

[COleConvertDialog](reference/coleconvertdialog-class.md)<br/>
Muestra el cuadro de diálogo convertir, la interfaz de usuario estándar para convertir elementos OLE de un tipo a otro.

[COlePropertiesDialog](reference/colepropertiesdialog-class.md)<br/>
Encapsula el cuadro de diálogo Propiedades comunes de OLE de Windows. Los cuadros de diálogo Propiedades comunes de OLE proporcionan una manera sencilla de mostrar y modificar las propiedades de un elemento de documento OLE de una manera coherente con los estándares de Windows.

[COleUpdateDialog](reference/coleupdatedialog-class.md)<br/>
Muestra el cuadro de diálogo actualizar, la interfaz de usuario estándar para actualizar todos los vínculos de un documento. El cuadro de diálogo contiene un indicador de progreso para indicar cómo se completa el procedimiento de actualización.

[COleChangeSourceDialog](reference/colechangesourcedialog-class.md)<br/>
Muestra el cuadro de diálogo cambiar origen, la interfaz de usuario estándar para cambiar el destino o el origen de un vínculo.

[COleBusyDialog](reference/colebusydialog-class.md)<br/>
Muestra los cuadros de diálogo servidor ocupado y servidor que no responde, la interfaz de usuario estándar para administrar las llamadas a aplicaciones ocupadas. Normalmente, la implementación muestra automáticamente `COleMessageFilter` .

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)
