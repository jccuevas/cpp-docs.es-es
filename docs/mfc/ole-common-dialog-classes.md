---
title: Clases de cuadro de diálogo comunes OLE | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.ole
dev_langs:
- C++
helpviewer_keywords:
- ActiveX classes [MFC]
- dialog classes [MFC], OLE
- OLE common dialog classes [MFC]
- common dialog classes [MFC]
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2e3cedbe3cd08a425bd2bde2b4a6ca8c5a493c72
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348109"
---
# <a name="ole-common-dialog-classes"></a>Clases de cuadros de diálogo comunes OLE
Estas clases controlen tareas comunes de OLE mediante la implementación de un número de cuadros de diálogo OLE estándar. También proporcionan una interfaz de usuario coherente para la funcionalidad OLE.  
  
 [COleDialog](../mfc/reference/coledialog-class.md)  
 Utiliza el marco de trabajo para contener las implementaciones comunes para todos los cuadros de diálogo OLE. Todas las clases de cuadro de diálogo de la categoría de la interfaz de usuario se derivan de esta clase base. `COleDialog` no se puede usar directamente.  
  
 [Clase COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)  
 Muestra el cuadro de diálogo Insertar objeto, la interfaz de usuario estándar para insertar nuevo OLE elementos vinculados o incrustados.  
  
 [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)  
 Muestra el cuadro de diálogo Pegado especial, la interfaz de usuario estándar para implementar el comando Editar Pegado especial.  
  
 [COleLinksDialog](../mfc/reference/colelinksdialog-class.md)  
 Muestra el cuadro de diálogo Editar vínculos, la interfaz de usuario estándar para modificar información sobre los elementos vinculados.  
  
 [Clase COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)  
 Muestra el cuadro de diálogo Cambiar icono, la interfaz de usuario estándar para cambiar el icono asociado a un OLE incrustado o el elemento vinculado.  
  
 [Clase COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)  
 Muestra el cuadro de diálogo de Convert, la interfaz de usuario estándar para convertir los elementos OLE de un tipo a otro.  
  
 [COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)  
 Encapsula el cuadro de diálogo de propiedades de OLE común de Windows. Cuadros de diálogo comunes OLE propiedades proporcionan una manera sencilla de mostrar y modificar las propiedades de un elemento de documento OLE de manera coherente con los estándares de Windows.  
  
 [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)  
 Muestra el cuadro de diálogo de actualización, la interfaz de usuario estándar para actualizar todos los vínculos en un documento. El cuadro de diálogo contiene un indicador de progreso para indicar la distancia es el procedimiento de actualización hasta su finalización.  
  
 [COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)  
 Muestra el cuadro de diálogo Cambiar origen, la interfaz de usuario estándar para cambiar el destino o el origen de un vínculo.  
  
 [Clase COleBusyDialog](../mfc/reference/colebusydialog-class.md)  
 Muestra los cuadros de diálogo servidor ocupado y el servidor no responde, la interfaz de usuario estándar para controlar las llamadas a las aplicaciones ocupadas. Habitualmente se muestra automáticamente el `COleMessageFilter` implementación.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

