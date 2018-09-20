---
title: Operadores de preprocesador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b80c9c8ef371808fc98d0475afc00223b13194ea
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384044"
---
# <a name="preprocessor-operators"></a>Operadores de preprocesador
Se utilizan cuatro operadores específicos del preprocesador en el contexto de la directiva `#define` (vea la lista siguiente para obtener un resumen de cada uno de ellos). En las próximas tres secciones se explican los operadores de generación de cadenas, generación de caracteres y pegado de token. Para obtener información sobre la `defined` operador, consulte [#if, #elif, #else y #endif directivas](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).  
  
|Operador|Acción|  
|--------------|------------|  
|[Stringizing (#) (operador)](../preprocessor/stringizing-operator-hash.md)|Hace que el argumento real correspondiente se delimite con comillas dobles|  
|[Operador charizing (#@)](../preprocessor/charizing-operator-hash-at.md)|Hace que el argumento correspondiente se delimite con comillas simples y se trate como un carácter (Específicos de Microsoft)|  
|[Operador de pegado de token (##)](../preprocessor/token-pasting-operator-hash-hash.md)|Permite concatenar tokens utilizados como argumentos reales para formar otros tokens|  
|[operador definido](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|Simplifica la escritura de expresiones compuestas en determinadas directivas de macro|  
  
## <a name="see-also"></a>Vea también  
 
[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)<br/>
[Macros predefinidas](../preprocessor/predefined-macros.md)<br/>
[Referencia del preprocesador de C/C++](../preprocessor/c-cpp-preprocessor-reference.md)