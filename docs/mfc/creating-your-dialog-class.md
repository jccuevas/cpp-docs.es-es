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
ms.openlocfilehash: fab75268e39d75b67db435ebb8d0af6c0b8371fd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620514"
---
# <a name="creating-your-dialog-class"></a>Creating Your Dialog (Clase)

Para cada cuadro de diálogo del programa, cree una nueva clase de cuadro de diálogo para que funcione con el recurso de cuadro de diálogo.

Al [Agregar una clase](../ide/adding-a-class-visual-cpp.md) se explica cómo crear una nueva clase de cuadro de diálogo. Cuando se crea una clase de cuadro de diálogo con el [Asistente para clases](reference/mfc-class-wizard.md), escribe los siguientes elementos en los archivos. h y. cpp que especifique:

En el archivo. h:

- Una declaración de clase para la clase de cuadro de diálogo. La clase se deriva de [CDialog](reference/cdialog-class.md).

En el archivo. cpp:

- Mapa de mensajes para la clase.

- Constructor estándar para el cuadro de diálogo.

- Una invalidación de la función miembro [DoDataExchange](reference/cwnd-class.md#dodataexchange) . Edite esta función. Se utiliza para la funcionalidad de intercambio y validación de datos de cuadros de diálogo, tal y como se describe más adelante en [intercambio y validación de datos de cuadro de diálogo](dialog-data-exchange-and-validation.md).

## <a name="see-also"></a>Consulte también

[Crear una clase de diálogo con los Asistentes para código](creating-a-dialog-class-with-code-wizards.md)<br/>
[Trabajar con cuadros de diálogo en MFC](life-cycle-of-a-dialog-box.md)
