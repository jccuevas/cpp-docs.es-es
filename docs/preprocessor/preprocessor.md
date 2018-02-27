---
title: Preprocesador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 75caab67343e7806e1dd97fb673114949c68a94c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="preprocessor"></a>Preprocesador
El preprocesador es un procesador de texto que manipula el texto de un archivo de código fuente como parte de la primera fase de traducción. El preprocesador no analiza el texto original, sino que lo divide en tokens con el fin de buscar llamadas a macros. Aunque el compilador invoca normalmente el preprocesador en el primer paso, también se puede invocar el preprocesador por separado para procesar el texto sin compilación.  
  
 El material de referencia del preprocesador incluye las siguientes secciones:  
  
-   [Directivas de preprocesador](../preprocessor/preprocessor-directives.md)  
  
-   [Operadores de preprocesador](../preprocessor/preprocessor-operators.md)  
  
-   [Macros predefinidas](../preprocessor/predefined-macros.md)  
  
-   [Pragmas](../preprocessor/pragma-directives-and-the-pragma-keyword.md)  
  
 **Específicos de Microsoft**  
  
 Puede obtener una lista de código fuente tras el preprocesamiento mediante la [/E](../build/reference/e-preprocess-to-stdout.md) o [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) opción del compilador. Ambas opciones invocan el preprocesador y envían el texto resultante al dispositivo de salida estándar que, en la mayoría de los casos, es la consola. La diferencia entre las dos opciones es que /E incluye las directivas `#line` y /EP elimina estas directivas.  
  
 **FIN de Específicos de Microsoft**  
  
##  <a name="_predir_special_terminology"></a> Terminología especial  
 En la documentación del preprocesador, el término “argumento” hace referencia a la entidad que se pasa a una función. En algunos casos, se cambia por “real” o “formal”, que describe la expresión de argumento especificada en la llamada de función y la declaración de argumento especificada en la definición de función, respectivamente.  
  
 El término “variable” hace referencia a un objeto de datos de tipo C. El término “objeto” hace referencia tanto a objetos como a variables de C++; es un término inclusivo.  
  
## <a name="see-also"></a>Vea también  
 [Referencia del preprocesador de C/c ++](../preprocessor/c-cpp-preprocessor-reference.md)   
 [Fases de traducción](../preprocessor/phases-of-translation.md)