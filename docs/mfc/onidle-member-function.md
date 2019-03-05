---
title: OnIdle Member (Función)
ms.date: 11/19/2018
f1_keywords:
- OnIdle
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
ms.openlocfilehash: c7cdd5cd2327be1b90e7fdb3694353acf8adcafe
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304458"
---
# <a name="onidle-member-function"></a>OnIdle Member (Función)

Cuando no se están procesando ningún mensaje de Windows, el marco llama a la [CWinApp](../mfc/reference/cwinapp-class.md) función miembro [OnIdle](../mfc/reference/cwinapp-class.md#onidle) (descrita en la referencia de la biblioteca de MFC).

Invalidar `OnIdle` para realizar tareas en segundo plano. La versión predeterminada actualiza el estado de los objetos de interfaz de usuario, como botones de barra de herramientas y realiza la limpieza de objetos temporales creados por el marco de trabajo en el transcurso de sus operaciones. La ilustración siguiente muestra cómo el bucle de mensajes llama `OnIdle` cuando hay mensajes en la cola.

![Proceso de bucle de mensajes](../mfc/media/vc387c1.gif "proceso de bucle de mensajes") <br/>
El bucle de mensajes

Para obtener más información sobre lo que puede hacer en el bucle de inactividad, consulte [procesamiento de bucles inactivos](../mfc/idle-loop-processing.md).

## <a name="see-also"></a>Vea también

[CWinApp: La clase de aplicación](../mfc/cwinapp-the-application-class.md)
