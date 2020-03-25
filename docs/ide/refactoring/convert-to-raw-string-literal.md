---
title: Convertir en literal de cadena sin formato
ms.date: 11/16/2016
ms.assetid: fffbfee4-66ee-42ba-aeb9-df07fb702c51
ms.openlocfilehash: 5636e00bfe8655d84fb2e4b64e0391324ab35d7d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171819"
---
# <a name="convert-to-raw-string-literal"></a>Convertir en literal de cadena sin formato

**Qué:** Permite convertir cualquier cadena en un literal de cadena sin formato de C++.

**Cuándo:** Tiene una cadena con caracteres de escape que no se deben procesar como caracteres de escape.

**Por qué:** Podría aplicar secuencias de escape doble a los caracteres, pero esto suele generar cadenas confusas e ilegibles.  El uso de literales de cadena sin formato hace que las cadenas sean mucho más fáciles de leer.

**Cómo:**

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
