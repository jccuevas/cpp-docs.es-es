---
title: Ciclo de vida de un cuadro de diálogo
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], life cycle
- modal dialog boxes [MFC], life cycle
- modeless dialog boxes [MFC], life cycle
- MFC dialog boxes [MFC], life cycle
- life cycle of dialog boxes [MFC]
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
ms.openlocfilehash: e92489499a3a5aaaf2fb97e8908cb30d5e168240
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577624"
---
# <a name="life-cycle-of-a-dialog-box"></a>Ciclo de vida de un cuadro de diálogo

Durante el ciclo de vida de un cuadro de diálogo, el usuario invoca el cuadro de diálogo, normalmente dentro de un controlador de comandos que crea e inicializa el objeto de cuadro de diálogo, el usuario interactúa con el cuadro de diálogo y cierra el cuadro de diálogo.

En los cuadros de diálogo modal, el controlador recopila los datos que el usuario ha especificado una vez que se cierra el cuadro de diálogo. Puesto que el objeto de cuadro de diálogo existe cuando se haya cerrado su ventana de cuadro de diálogo, simplemente puede usar las variables de miembro de la clase de cuadro de diálogo para extraer los datos.

En los cuadros de diálogo no modal, a menudo puede extraer datos desde el objeto de cuadro de diálogo mientras el cuadro de diálogo sigue estando visible. En algún momento, se destruye el objeto de cuadro de diálogo; Cuando esto sucede dependerá del código.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Crear y mostrar cuadros de diálogo](../mfc/creating-and-displaying-dialog-boxes.md)

- [Crear cuadros de diálogo modal](../mfc/creating-modal-dialog-boxes.md)

- [Crear cuadros de diálogo no modal](../mfc/creating-modeless-dialog-boxes.md)

- [Mediante una plantilla de cuadro de diálogo en memoria](../mfc/using-a-dialog-template-in-memory.md)

- [Establecer el color de fondo del cuadro de diálogo](../mfc/setting-the-dialog-boxs-background-color.md)

- [Inicializar el cuadro de diálogo](../mfc/initializing-the-dialog-box.md)

- [Controlar mensajes de Windows en el cuadro de diálogo](../mfc/handling-windows-messages-in-your-dialog-box.md)

- [Recuperación de datos desde el objeto de cuadro de diálogo](../mfc/retrieving-data-from-the-dialog-object.md)

- [Cierre el cuadro de diálogo](../mfc/closing-the-dialog-box.md)

- [Destruir el cuadro de diálogo](../mfc/destroying-the-dialog-box.md)

- [Intercambio de datos de cuadro de diálogo (DDX) y la validación (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [Cuadros de diálogo de hoja de propiedades](../mfc/property-sheets-and-property-pages-mfc.md)

## <a name="see-also"></a>Vea también

[Cuadros de diálogo](../mfc/dialog-boxes.md)

