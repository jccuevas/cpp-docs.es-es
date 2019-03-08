---
title: Clases de cuadros de diálogo comunes OLE
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- dialog classes [MFC], OLE
- OLE common dialog classes [MFC]
- common dialog classes [MFC]
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
ms.openlocfilehash: d34c141fc9a2b53eab6a4c0b0ce1799ff5243d84
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263551"
---
# <a name="ole-common-dialog-classes"></a>Clases de cuadros de diálogo comunes OLE

Estas clases controlan las tareas comunes de OLE mediante la implementación de una serie de cuadros de diálogo OLE estándares. También proporcionan una interfaz de usuario coherente para la funcionalidad OLE.

[COleDialog](../mfc/reference/coledialog-class.md)<br/>
Usa el marco de trabajo para contener las implementaciones comunes para todos los cuadros de diálogo OLE. Todas las clases de cuadro de diálogo en la categoría de la interfaz de usuario se derivan de esta clase base. `COleDialog` no se puede usar directamente.

[COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)<br/>
Muestra el cuadro de diálogo Insertar objeto la interfaz de usuario estándar para insertar nuevo OLE elementos vinculados o incrustados.

[COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)<br/>
Muestra el cuadro de diálogo Pegado especial, la interfaz de usuario estándar para implementar el comando Editar Pegado especial.

[COleLinksDialog](../mfc/reference/colelinksdialog-class.md)<br/>
Muestra el cuadro de diálogo Editar vínculos, la interfaz de usuario estándar para modificar la información sobre los elementos vinculados.

[COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)<br/>
Muestra el cuadro de diálogo Cambiar icono, la interfaz de usuario estándar para cambiar el icono asociado a un OLE incrustado o el elemento vinculado.

[COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)<br/>
Muestra el cuadro de diálogo Convertir, la interfaz de usuario estándar para convertir los elementos OLE.

[COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)<br/>
Encapsula el cuadro de diálogo Propiedades de OLE común de Windows. Cuadros de diálogo comunes OLE propiedades proporcionan una manera fácil para mostrar y modificar las propiedades de un elemento de documento OLE de manera coherente con los estándares de Windows.

[COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)<br/>
Muestra el cuadro de diálogo de actualización, la interfaz de usuario estándar para actualizar todos los vínculos en un documento. El cuadro de diálogo contiene un indicador de progreso para indicar cómo cerrar el procedimiento de actualización es hasta su finalización.

[COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)<br/>
Muestra el cuadro de diálogo Cambiar origen, la interfaz de usuario estándar para cambiar el destino o el origen de un vínculo.

[COleBusyDialog](../mfc/reference/colebusydialog-class.md)<br/>
Muestra los cuadros de diálogo servidor ocupado y el servidor no responde, la interfaz de usuario estándar para controlar las llamadas a las aplicaciones ocupadas. Normalmente, se muestra automáticamente el `COleMessageFilter` implementación.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)
