---
title: Operadores de preprocesador | Documentos de Microsoft
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
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 551b2c3ba8a5055fc6b6dfd1b94c461c37e72209
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="preprocessor-operators"></a>Operadores de preprocesador
Se utilizan cuatro operadores específicos del preprocesador en el contexto de la directiva `#define` (vea la lista siguiente para obtener un resumen de cada uno de ellos). En las próximas tres secciones se explican los operadores de generación de cadenas, generación de caracteres y pegado de token. Para obtener información sobre la **definido** (operador), consulte [#if, #elif, #else y #endif directivas](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).  
  
|Operador|Acción|  
|--------------|------------|  
|[Generación de cadenas (#) (operador)](../preprocessor/stringizing-operator-hash.md)|Hace que el argumento real correspondiente se delimite con comillas dobles|  
|[Operador charizing (#@)](../preprocessor/charizing-operator-hash-at.md)|Hace que el argumento correspondiente se delimite con comillas simples y se trate como un carácter (Específicos de Microsoft)|  
|[Operador de pegado de token (##)](../preprocessor/token-pasting-operator-hash-hash.md)|Permite concatenar tokens utilizados como argumentos reales para formar otros tokens|  
|[operador definido](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|Simplifica la escritura de expresiones compuestas en determinadas directivas de macro|  
  
## <a name="see-also"></a>Vea también  
 [Directivas de preprocesador](../preprocessor/preprocessor-directives.md)   
 [Macros predefinidas](../preprocessor/predefined-macros.md)   
 [Referencia del preprocesador de C/C++](../preprocessor/c-cpp-preprocessor-reference.md)