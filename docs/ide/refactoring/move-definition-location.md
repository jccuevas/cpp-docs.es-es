---
title: Mover ubicación de definición | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: c6d507ac-c61e-4da2-95c8-d504b42e2520
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44211105429e33c136999a7877ac6ee42af29f17
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327845"
---
# <a name="move-definition-location"></a>Mover ubicación de definición
**Qué:** permite mover una definición de función de manera inmediata al archivo de encabezado correspondiente.

**Cuándo:** tiene una función que quiere mover a un archivo de encabezado.  

**Por qué:** podría mover manualmente la función, pero esta característica la moverá de forma automática, y creará el archivo de encabezado si es necesario.

**Cómo**:

1. coloque el cursor de texto o el ratón sobre la función que quiera mover.

   ![Código resaltado](images/movedefinition_highlight.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Mover ubicación de definición** en el menú contextual.
   * **Mouse**
     * Haga clic con el botón derecho en el menú **Acciones rápidas y refactorizaciones** y seleccione **Mover ubicación de definición** en el menú contextual.

1. La función se moverá al archivo de encabezado correspondiente, que verá en una ventana de vista previa emergente.  Si el archivo de encabezado no existe, también se creará y se incluirá en el proyecto.

   ![Resultado de crear la declaración o definición](images/movedefinition_result.png)
