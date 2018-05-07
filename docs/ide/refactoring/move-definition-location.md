---
title: Mover la ubicación de definición | Documentos de Microsoft
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="move-definition-location"></a>Mover ubicación de definición
**¿Qué:** le permite moverse de inmediato una definición de función en el archivo de encabezado correspondiente.

**Cuándo:** tiene una función que desea mover a un archivo de encabezado.  

**Por este motivo:** podría mover manualmente la función, pero esta característica lo moverá automáticamente, crear el archivo de encabezado si es necesario.

**Cómo**:

1. Coloque el cursor de texto o el mouse sobre la función para la que desea mover.

   ![Código resaltado](images/movedefinition_highlight.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **mover la ubicación de definición de** en el menú contextual.
   * **Mouse**
     * Haga clic en y seleccione el **acciones rápidas y refactorizaciones** menú y seleccione **mover la ubicación de definición de** en el menú contextual.

1. La función se va a mover el archivo de encabezado correspondiente, que verá en una ventana de vista previa emergente.  Si no existe el archivo de encabezado, se también se crean y se incluirán en el proyecto.

   ![Crear declaración / definición dar como resultado](images/movedefinition_result.png)
