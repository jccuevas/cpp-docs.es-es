---
title: "Función extraer | Documentos de Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e31d1249-9705-4511-acbd-9f6fe73bdf2d
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dbcd323292e301857c65d908047ab14948b86573
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="extract-function"></a>Función extraer
**¿Qué:** le permite convertir un fragmento de código en su propia función.

**Cuándo:** tiene un fragmento de código existente en alguna función que debe llamarse desde otra función.  

**Por este motivo:** se puede copiar y pegar ese código, pero esto conduciría a la duplicación.  Una solución mejor es refactorizar ese fragmento a su propia función que se puede llamar libremente por cualquier otra función.

**Cómo:**

1. Resalte el código que se va a extraer:

   ![Código que aparece resaltado](images/extractfunction_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl + R**, a continuación, **Ctrl + M**.  (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **función extraer (Experimental)** en el menú contextual.
   * **Mouse**
     * Seleccione **Editar > refactorizar > Extraer función (Experimental)**.
     * Haga clic en el código, seleccione la **acciones rápidas y refactorizaciones** menú y seleccione **función extraer (Experimental)** en el menú contextual.
     * Haga clic en el ![bombilla](images/bulb.png) icono que aparece en el margen izquierdo y seleccione **función extraer (Experimental)** en el menú contextual.

1. En el **extraer función o un método (Experimental)** ventana, escriba el nuevo nombre de función, seleccione dónde desea que el código va a colocar y haga clic en el **Aceptar** botón.  

   ![Extraer (función)](images/extractfunction_dialog.png)

1. Se creará la nueva función que ha especificado, un prototipo de función en el archivo de encabezado correspondiente, y el código original se cambiarán para llamar a esa función.

   ![Extraer el resultado de la función](images/extractfunction_result.png)