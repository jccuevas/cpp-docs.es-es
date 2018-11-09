---
title: Crear declaración o definición
ms.date: 10/19/2018
ms.assetid: 6b1cdcb2-765e-4b93-8cef-92b861f64eba
ms.openlocfilehash: 56f15ba040314b07450dc8730a913a18361e092f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456971"
---
# <a name="create-declaration--definition"></a>Crear declaración o definición
**Qué:** Permite generar inmediatamente la declaración o definición de una función.

**Caso**: Tiene una función que necesita una declaración, o viceversa.

**Por qué:** Podría crear manualmente la definición o declaración, pero esto la creará de manera automática, creando el archivo de encabezado o código si es necesario.

**Cómo**:

1. Coloque el cursor de texto o el ratón sobre la función para la que quiera crear la declaración o definición.

   ![Código resaltado](images/createdefinition_highlight.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Crear declaración o definición** en el menú contextual.
   * **Mouse**
     * Haga clic con el botón derecho en el menú **Acciones rápidas y refactorizaciones** y seleccione **Crear declaración o definición** en el menú contextual.

1. Se creará la declaración o definición de la función en el archivo de código fuente o de encabezado, que verá en una ventana de vista previa emergente.  Si el archivo de código fuente o de encabezado no existe, también se creará y se incluirá en el proyecto.

   ![Resultado de crear la declaración o definición](images/createdefinition_result.png)
