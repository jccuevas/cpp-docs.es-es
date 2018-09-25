---
title: Convertir en literal de cadena sin formato | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: fffbfee4-66ee-42ba-aeb9-df07fb702c51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75037ea542a5bd2160d9a89138b12f82867002a5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388451"
---
# <a name="convert-to-raw-string-literal"></a>Convertir en literal de cadena sin formato
**Qué:** Permite convertir cualquier cadena en un literal de cadena sin formato de C++.

**Cuándo:** Tiene una cadena con caracteres de escape que no se deben procesar como caracteres de escape.

**Por qué:** Podría aplicar secuencias de escape doble a los caracteres, pero esto suele generar cadenas confusas e ilegibles.  El uso de literales de cadena sin formato hace que las cadenas sean mucho más fáciles de leer.

**Cómo**:

1. Coloque el cursor de texto o el ratón sobre la cadena de escape que se va a convertir.

   ![Código resaltado](images/stringliteral_highlight.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Convertir en literal de cadena sin formato** en el menú contextual.
   * **Mouse**
     * Haga clic con el botón derecho sobre el código, seleccione el menú **Acciones rápidas y refactorizaciones** y seleccione **Convertir en literal de cadena sin formato** en el menú contextual.
     * Haga clic en el icono ![Bombilla](images/bulb.png) que aparece en el margen izquierdo y seleccione **Convertir en literal de cadena sin formato** en el menú contextual.

1. La cadena se convertirá inmediatamente en un literal de cadena sin formato.

   ![Resultado del literal de cadena sin formato](images/stringliteral_result.png)