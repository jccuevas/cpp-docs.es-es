---
title: "Función miembro OnIdle | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OnIdle
dev_langs: C++
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4dfbc0a1f20cb6cc01143ed6f07a63e84b53be6b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="onidle-member-function"></a>OnIdle Member (Función)
Cuando no se están procesando ningún mensaje de Windows, el marco llama a la [CWinApp](../mfc/reference/cwinapp-class.md) función miembro [OnIdle](../mfc/reference/cwinapp-class.md#onidle) (que se describe en la referencia de la biblioteca de MFC).  
  
 Invalidar `OnIdle` para realizar tareas en segundo plano. La versión predeterminada actualiza el estado de los objetos de interfaz de usuario, como botones de barra de herramientas y realiza la limpieza de los objetos temporales creados por el marco de trabajo en el transcurso de sus operaciones. La ilustración siguiente muestra cómo se llama el bucle de mensajes `OnIdle` cuando no hay ningún mensaje en la cola.  
  
 ![Proceso de bucle de mensajes](../mfc/media/vc387c1.gif "vc387c1")  
El bucle de mensajes  
  
 Para obtener más información sobre lo que puede hacer en el bucle inactivo, vea [procesamiento de bucles inactivos](../mfc/idle-loop-processing.md).  
  
## <a name="see-also"></a>Vea también  
 [CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)
