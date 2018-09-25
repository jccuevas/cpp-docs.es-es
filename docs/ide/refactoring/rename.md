---
title: Cambiar nombre | Microsoft Docs
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
ms.openlocfilehash: 7a00eed341e0fc1ca8573e2f66744ea04055f259
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399217"
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

1. En la ventana **Cambiar nombre** que aparece, escriba el nombre nuevo para el elemento seleccionado y haga clic en el botón **Vista previa**.  Cambie el **Ámbito de búsqueda** si quiere ampliar o reducir el ámbito del cambio de nombre.

   ![Cuadro de diálogo Cambiar nombre](images/rename_dialog.png)

   > [!TIP]
   > Puede omitir la vista previa si activa la opción **Omitir la vista previa de los cambios si todas las referencias están confirmadas**.

1. Cuando aparezca la ventana **Obtener vista previa de cambios - Cambiar nombre**, asegúrese de que los cambios que está solicitando se están realizando de manera correcta.  Use las casillas de la mitad superior de la ventana para habilitar o deshabilitar el cambio de nombre de cualquier elemento.

   ![Vista previa de Cambiar nombre](images/rename_preview.png)

1. Cuando todo parezca correcto, haga clic en el botón **Aplicar** y se cambiará el nombre del elemento en el código fuente.
