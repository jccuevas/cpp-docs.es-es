---
title: Función miembro OnIdle | Documentos de Microsoft
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
ms.openlocfilehash: bbe912db448e424f18b6d72f6e148312c5940687
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350372"
---
# <a name="onidle-member-function"></a>OnIdle Member (Función)
Cuando no se están procesando ningún mensaje de Windows, el marco llama a la [CWinApp](../mfc/reference/cwinapp-class.md) función miembro [OnIdle](../mfc/reference/cwinapp-class.md#onidle) (que se describe en la referencia de la biblioteca de MFC).  
  
 Invalidar `OnIdle` para realizar tareas en segundo plano. La versión predeterminada actualiza el estado de los objetos de interfaz de usuario, como botones de barra de herramientas y realiza la limpieza de los objetos temporales creados por el marco de trabajo en el transcurso de sus operaciones. La ilustración siguiente muestra cómo se llama el bucle de mensajes `OnIdle` cuando no hay ningún mensaje en la cola.  
  
 ![Proceso de bucle de mensajes](../mfc/media/vc387c1.gif "vc387c1")  
El bucle de mensajes  
  
 Para obtener más información sobre lo que puede hacer en el bucle inactivo, vea [procesamiento de bucles inactivos](../mfc/idle-loop-processing.md).  
  
## <a name="see-also"></a>Vea también  
 [CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)
