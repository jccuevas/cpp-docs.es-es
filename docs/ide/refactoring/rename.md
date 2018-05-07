---
title: Cambiar el nombre | Documentos de Microsoft
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: 64b42a88-3bd9-4399-8b96-75bceffc353b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a064527f6afcbf91be3fb4e51180be647c1f506
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="rename"></a>Cambiar nombre
**Qué:** Le permite cambiar el nombre de los identificadores de símbolos de código, como campos, variables locales, métodos, espacios de nombres, propiedades y tipos.

**Cuándo:** Desea cambiar con seguridad algo sin tener que buscar todas las instancias y copiar y pegar el nuevo nombre.  

**Por qué:** Es probable que copiar y pegar el nuevo nombre en todo un proyecto dé lugar a errores.  Esta herramienta de refactorización llevará a cabo con precisión la acción de cambio de nombre.

**Cómo**:

1. Resalte o coloque el cursor de texto dentro del elemento cuyo nombre se va a cambiar:

   ![Código resaltado](images/rename_highlight.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **CTRL+R** y, a continuación, **CTRL+R**.  (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
   * **Mouse**
     * Seleccione **Editar > Refactorizar > Cambiar nombre**.
     * Haga clic con el botón derecho en el código y seleccione **Cambiar nombre**.

1. En el **cambiar el nombre de** ventana que aparece, escriba el nuevo nombre para el elemento seleccionado y haga clic en el **vista previa** botón.  Cambiar el **ámbito de búsqueda** si desea ampliar o reducir el ámbito del cambio de nombre.

   ![cambiar el nombre de cuadro de diálogo](images/rename_dialog.png)

   > [!TIP]
   > Puede omitir la vista previa activando el **vista previa de Skip cambia si las referencias se confirman** opción.

1. Cuando el **cambiar el nombre de vista previa de cambios -** muestra la ventana, asegúrese de que los cambios que está solicitando se están realizando correctamente.  Utilice las casillas de verificación en la mitad superior de la ventana para habilitar o deshabilitar el cambio de nombre de cualquier elemento.

   ![Cambiar el nombre de vista previa](images/rename_preview.png)

1. Si todo es correcto, haga clic en el **aplicar** botón y el elemento se cambiará en el código fuente.
