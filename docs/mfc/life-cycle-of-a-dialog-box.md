---
title: Trabajar con cuadros de diálogo en MFC
ms.date: 09/27/2019
helpviewer_keywords:
- dialog boxes [MFC], life cycle
- modal dialog boxes [MFC], life cycle
- modeless dialog boxes [MFC], life cycle
- MFC dialog boxes [MFC], life cycle
- life cycle of dialog boxes [MFC]
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
ms.openlocfilehash: d365be21ef19a6779df649e9368fdc0cda4851df
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621448"
---
# <a name="working-with-dialog-boxes-in-mfc"></a>Trabajar con cuadros de diálogo en MFC

Durante el ciclo de vida de un cuadro de diálogo, el usuario invoca el cuadro de diálogo, normalmente dentro de un controlador de comandos que crea e inicializa el objeto de diálogo, el usuario interactúa con el cuadro de diálogo y, a continuación, se cierra el cuadro de diálogo.

En los cuadros de diálogo modales, el controlador recopila los datos que el usuario especificó una vez que se cierra el cuadro de diálogo. Puesto que el objeto de cuadro de diálogo existe después de cerrarse su ventana de diálogo, puede usar simplemente las variables miembro de la clase de cuadro de diálogo para extraer los datos.

En el caso de los cuadros de diálogo no modales, a menudo puede extraer datos del objeto de cuadro de diálogo mientras el cuadro de diálogo todavía está visible. En algún momento, el objeto de cuadro de diálogo se destruye; Cuando esto sucede, depende del código.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Crear y mostrar cuadros de diálogo](creating-and-displaying-dialog-boxes.md)

- [Crear cuadros de diálogo modales](creating-modal-dialog-boxes.md)

- [Crear cuadros de diálogo no modales](creating-modeless-dialog-boxes.md)

- [Uso de una plantilla de cuadro de diálogo en memoria](using-a-dialog-template-in-memory.md)

- [Establecer el color de fondo del cuadro de diálogo](setting-the-dialog-boxs-background-color.md)

- [Inicializar el cuadro de diálogo](initializing-the-dialog-box.md)

- [Controlar mensajes de Windows en el cuadro de diálogo](handling-windows-messages-in-your-dialog-box.md)

- [Recuperar datos del objeto de cuadro de diálogo](retrieving-data-from-the-dialog-object.md)

- [Cerrar el cuadro de diálogo](closing-the-dialog-box.md)

- [Destruir el cuadro de diálogo](destroying-the-dialog-box.md)

- [Intercambio de datos de cuadros de diálogo (DDX) y validación (DDV)](dialog-data-exchange-and-validation.md)

- [Cuadros de diálogo de hoja de propiedades](property-sheets-and-property-pages-mfc.md)

## <a name="see-also"></a>Consulte también

[Cuadros de diálogo](dialog-boxes.md)
