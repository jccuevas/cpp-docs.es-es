---
title: Función miembro OnIdle | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- OnIdle
dev_langs:
- C++
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b334a4561af40b69bc367ab5b1129afa8fb29ae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377304"
---
# <a name="onidle-member-function"></a>OnIdle Member (Función)

Cuando no se están procesando ningún mensaje de Windows, el marco llama a la [CWinApp](../mfc/reference/cwinapp-class.md) función miembro [OnIdle](../mfc/reference/cwinapp-class.md#onidle) (descrita en la referencia de la biblioteca de MFC).

Invalidar `OnIdle` para realizar tareas en segundo plano. La versión predeterminada actualiza el estado de los objetos de interfaz de usuario, como botones de barra de herramientas y realiza la limpieza de objetos temporales creados por el marco de trabajo en el transcurso de sus operaciones. La ilustración siguiente muestra cómo el bucle de mensajes llama `OnIdle` cuando hay mensajes en la cola.

![Proceso de bucle de mensajes](../mfc/media/vc387c1.gif "vc387c1") el bucle de mensajes

Para obtener más información sobre lo que puede hacer en el bucle de inactividad, consulte [procesamiento de bucles inactivos](../mfc/idle-loop-processing.md).

## <a name="see-also"></a>Vea también

[CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)
