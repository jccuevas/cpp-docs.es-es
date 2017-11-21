---
title: Cambiar el nombre | Documentos de Microsoft
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64b42a88-3bd9-4399-8b96-75bceffc353b
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d8e4152a1c920a243be9d4aa23712420893e29f5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="rename"></a>Cambiar nombre
**¿Qué:** le permite cambiar el nombre de los identificadores de símbolos de código, como campos, variables locales, métodos, espacios de nombres, propiedades y tipos.

**Cuándo:** desea cambiar con seguridad algo sin tener que buscar todas las instancias y copiar y pegar el nuevo nombre.  

**Por este motivo:** copiar y pegar el nuevo nombre en todo un proyecto es probable que podría dar lugar a errores.  Esta herramienta de refactorización con precisión llevará a cabo la acción de cambio de nombre.

**Cómo:**

1. Resalte o coloque el cursor de texto dentro del elemento que se va a cambiar:

   ![Código que aparece resaltado](images/rename_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl + R**, a continuación, **Ctrl + R**.  (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
   * **Mouse**
     * Seleccione **Editar > refactorizar > cambiar el nombre de**.
     * Haga clic en el código y seleccione **cambiar el nombre de**.

1. En el **cambiar el nombre de** ventana que aparece, escriba el nuevo nombre para el elemento seleccionado y haga clic en el **vista previa** botón.  Cambiar el **ámbito de búsqueda** si desea ampliar o reducir el ámbito del cambio de nombre.

   ![cambiar el nombre de cuadro de diálogo](images/rename_dialog.png)

   > [!TIP]
   > Puede omitir la vista previa activando el **vista previa de Skip cambia si las referencias se confirman** opción.

1. Cuando el **cambiar el nombre de vista previa de cambios -** muestra la ventana, asegúrese de que los cambios que está solicitando se están realizando correctamente.  Utilice las casillas de verificación en la mitad superior de la ventana para habilitar o deshabilitar el cambio de nombre de cualquier elemento.

   ![Cambiar el nombre de vista previa](images/rename_preview.png)

1. Si todo es correcto, haga clic en el **aplicar** botón y el elemento se cambiará en el código fuente.
