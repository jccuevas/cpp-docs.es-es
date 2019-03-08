---
title: Mover ubicación de definición
ms.date: 11/16/2016
ms.assetid: c6d507ac-c61e-4da2-95c8-d504b42e2520
ms.openlocfilehash: 7957e18732dfae92b7b3ae9cf7ecea441fc3a6b4
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693210"
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
