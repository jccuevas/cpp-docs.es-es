---
title: Convertir en Literal de cadena sin formato | Documentos de Microsoft
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
ms.openlocfilehash: b98825719e7b3c0d8eb760a2ec50644b5eddd54e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="convert-to-raw-string-literal"></a>Convertir en literal de cadena sin formato
**¿Qué:** le permite convertir cualquier cadena en una cadena sin formato de C++ literal.

**Cuándo:** tiene una cadena con caracteres de escape que no debe procesarse como caracteres de escape.

**Por este motivo:** pudo caracteres de doble escape, pero a menudo hace que las cadenas confusas y no se puede leer.  Usan literales de cadena sin formato hace que las cadenas son mucho más fáciles de leer.

**Cómo**:

1. Coloque el cursor de texto o el mouse sobre la cadena de escape para convertir.

   ![Código resaltado](images/stringliteral_highlight.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **convertir en Literal de cadena sin formato** en el menú contextual.
   * **Mouse**
     * Haga clic en el código, seleccione la **acciones rápidas y refactorizaciones** menú y seleccione **convertir en Literal de cadena sin formato** en el menú contextual.
     * Haga clic en el ![bombilla](images/bulb.png) icono que aparece en el margen izquierdo y seleccione **convertir en Literal de cadena sin formato** en el menú contextual.

1. La cadena se convertirán inmediatamente en un literal de cadena sin formato.  

   ![Resultado Literal de cadena sin formato](images/stringliteral_result.png)