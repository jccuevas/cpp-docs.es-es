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
ms.openlocfilehash: 17595713f942c7fe7784fa2a12adbcc583cad418
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619847"
---
# <a name="onidle-member-function"></a>OnIdle Member (Función)

Cuando no se están procesando mensajes de Windows, el marco de trabajo llama a la función miembro de [CWinApp](reference/cwinapp-class.md) [OnIdle](reference/cwinapp-class.md#onidle) (descrita en la referencia de la biblioteca MFC).

Invalide `OnIdle` para realizar tareas en segundo plano. La versión predeterminada actualiza el estado de los objetos de la interfaz de usuario, como los botones de la barra de herramientas, y realiza la limpieza de los objetos temporales creados por el marco de trabajo en el transcurso de sus operaciones. En la ilustración siguiente se muestra cómo el bucle de mensajes llama a cuando no hay `OnIdle` ningún mensaje en la cola.

![Proceso de bucle de mensajes](../mfc/media/vc387c1.gif "Proceso de bucle de mensajes") <br/>
El bucle de mensajes

Para obtener más información sobre lo que puede hacer en el bucle inactivo, consulte [procesamiento de bucles inactivos](idle-loop-processing.md).

## <a name="see-also"></a>Consulte también

[CWinApp: la clase Application](cwinapp-the-application-class.md)
