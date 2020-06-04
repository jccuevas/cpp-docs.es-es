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
ms.openlocfilehash: ad15250cf9a8dd663072cf9423263260bbb40a0e
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685728"
---
# <a name="working-with-dialog-boxes-in-mfc"></a>Trabajar con cuadros de diálogo en MFC

Durante el ciclo de vida de un cuadro de diálogo, el usuario invoca el cuadro de diálogo, normalmente dentro de un controlador de comandos que crea e inicializa el objeto de diálogo, el usuario interactúa con el cuadro de diálogo y, a continuación, se cierra el cuadro de diálogo.

En los cuadros de diálogo modales, el controlador recopila los datos que el usuario especificó una vez que se cierra el cuadro de diálogo. Puesto que el objeto de cuadro de diálogo existe después de cerrarse su ventana de diálogo, puede usar simplemente las variables miembro de la clase de cuadro de diálogo para extraer los datos.

En el caso de los cuadros de diálogo no modales, a menudo puede extraer datos del objeto de cuadro de diálogo mientras el cuadro de diálogo todavía está visible. En algún momento, el objeto de cuadro de diálogo se destruye; Cuando esto sucede, depende del código.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Crear y mostrar cuadros de diálogo](../mfc/creating-and-displaying-dialog-boxes.md)

- [Crear cuadros de diálogo modales](../mfc/creating-modal-dialog-boxes.md)

- [Crear cuadros de diálogo no modales](../mfc/creating-modeless-dialog-boxes.md)

- [Usar una plantilla de cuadro de diálogo en memoria](../mfc/using-a-dialog-template-in-memory.md)

- [Establecer el color de fondo del cuadro de diálogo](../mfc/setting-the-dialog-boxs-background-color.md)

- [Inicializar el cuadro de diálogo](../mfc/initializing-the-dialog-box.md)

- [Controlar mensajes de Windows en el cuadro de diálogo](../mfc/handling-windows-messages-in-your-dialog-box.md)

- [Recuperar datos del objeto de cuadro de diálogo](../mfc/retrieving-data-from-the-dialog-object.md)

- [Cerrar el cuadro de diálogo](../mfc/closing-the-dialog-box.md)

- [Destruir el cuadro de diálogo](../mfc/destroying-the-dialog-box.md)

- [Intercambio de datos de cuadros de diálogo (DDX) y validación (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [Cuadros de diálogo de hoja de propiedades](../mfc/property-sheets-and-property-pages-mfc.md)

## <a name="see-also"></a>Vea también

[Cuadros de diálogo](../mfc/dialog-boxes.md)
