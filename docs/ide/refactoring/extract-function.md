---
title: Extraer función | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333162"
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

   ![Función Extraer función](images/extractfunction_dialog.png)

1. La función nueva se creará donde haya especificado, un prototipo de función en el archivo de encabezado correspondiente, y el código original se cambiará para llamar a esa función.

   ![Extraer el resultado de la función](images/extractfunction_result.png)