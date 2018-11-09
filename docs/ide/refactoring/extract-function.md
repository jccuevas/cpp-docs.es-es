---
title: Extraer función
ms.date: 11/16/2016
ms.assetid: e31d1249-9705-4511-acbd-9f6fe73bdf2d
ms.openlocfilehash: 41a488b067bce750224f3785e311f91d43dc31ca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571033"
---
# <a name="extract-function"></a>Extraer función
**Qué:** permite convertir un fragmento de código en su propia función.

**Cuándo:** tiene un fragmento de código existente en alguna función que se debe llamar desde otra.

**Por qué:** Podría copiar y pegar ese código, pero esto provocaría una duplicación.  Una mejor solución consiste en refactorizar ese fragmento en su propia función a la que cualquier otra puede llamar libremente.

**Cómo**:

1. Resalte el código que se va a extraer:

   ![Código resaltado](images/extractfunction_highlight.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **CTRL+R** y, a continuación, **CTRL+M**.  (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Extraer función (experimental)** en el menú contextual.
   * **Mouse**
     * Seleccione **Editar > Refactorizar > Extraer función (Experimental)**.
     * Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y seleccione **Extraer función (experimental)** en el menú contextual.
     * Haga clic en el icono ![Bombilla](images/bulb.png) que aparece en el margen izquierdo y seleccione **Extraer función (experimental)** en el menú contextual.

1. En la ventana **Extraer función/método (experimental)**, escriba el nombre de función nuevo, seleccione dónde quiere colocar el código y haga clic en el botón **Aceptar**.

   ![Extraer el diálogo de la función](images/extractfunction_dialog.png)

1. La función nueva se creará donde haya especificado, un prototipo de función en el archivo de encabezado correspondiente, y el código original se cambiará para llamar a esa función.

   ![Extraer el resultado de la función](images/extractfunction_result.png)
