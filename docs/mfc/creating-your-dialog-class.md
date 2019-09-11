---
title: Creating Your Dialog (Clase)
ms.date: 09/06/2019
helpviewer_keywords:
- dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- files [MFC], creating
- dialog classes [MFC], Add Class Wizard
- dialog classes [MFC], creating
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
ms.openlocfilehash: 424d18196063456245e2a4841b42e6e447bded17
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907327"
---
# <a name="creating-your-dialog-class"></a>Creating Your Dialog (Clase)

Para cada cuadro de diálogo del programa, cree una nueva clase de cuadro de diálogo para que funcione con el recurso de cuadro de diálogo.

Al [Agregar una clase](../ide/adding-a-class-visual-cpp.md) se explica cómo crear una nueva clase de cuadro de diálogo. Cuando se crea una clase de cuadro de diálogo con el [Asistente para clases](reference/mfc-class-wizard.md), escribe los siguientes elementos en los archivos. h y. cpp que especifique:

En el archivo. h:

- Una declaración de clase para la clase de cuadro de diálogo. La clase se deriva de [CDialog](../mfc/reference/cdialog-class.md).

En el archivo. cpp:

- Mapa de mensajes para la clase.

- Constructor estándar para el cuadro de diálogo.

- Una invalidación de la función miembro [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) . Edite esta función. Se utiliza para la funcionalidad de intercambio y validación de datos de cuadros de diálogo, tal y como se describe más adelante en [intercambio y validación de datos de cuadro de diálogo](../mfc/dialog-data-exchange-and-validation.md).

## <a name="see-also"></a>Vea también

[Creación de una clase de diálogo con los Asistentes para código](../mfc/creating-a-dialog-class-with-code-wizards.md)<br/>
[Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)
