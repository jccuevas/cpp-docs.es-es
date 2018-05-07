---
title: Función extraer | Documentos de Microsoft
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: e31d1249-9705-4511-acbd-9f6fe73bdf2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fc4d48c972bca9352f326085574e4cf4df83aea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="extract-function"></a>Función extraer
**¿Qué:** le permite convertir un fragmento de código en su propia función.

**Cuándo:** tiene un fragmento de código existente en alguna función que debe llamarse desde otra función.  

**Por qué:** Podría copiar y pegar ese código, pero esto provocaría una duplicación.  Una solución mejor es refactorizar ese fragmento a su propia función que se puede llamar libremente por cualquier otra función.

**Cómo**:

1. Resalte el código que se va a extraer:

   ![Código resaltado](images/extractfunction_highlight.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **CTRL+R** y, a continuación, **CTRL+M**.  (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **función extraer (Experimental)** en el menú contextual.
   * **Mouse**
     * Seleccione **Editar > refactorizar > Extraer función (Experimental)**.
     * Haga clic en el código, seleccione la **acciones rápidas y refactorizaciones** menú y seleccione **función extraer (Experimental)** en el menú contextual.
     * Haga clic en el ![bombilla](images/bulb.png) icono que aparece en el margen izquierdo y seleccione **función extraer (Experimental)** en el menú contextual.

1. En el **extraer función o un método (Experimental)** ventana, escriba el nuevo nombre de función, seleccione dónde desea que el código va a colocar y haga clic en el **Aceptar** botón.  

   ![Extraer (función)](images/extractfunction_dialog.png)

1. Se creará la nueva función que ha especificado, un prototipo de función en el archivo de encabezado correspondiente, y el código original se cambiarán para llamar a esa función.

   ![Extraer el resultado de la función](images/extractfunction_result.png)