---
title: Error del evaluador de expresiones CXX0039 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0039
dev_langs:
- C++
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8681d73d2889433516b205a47c500193bbeabdb0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="expression-evaluator-error-cxx0039"></a>Error del evaluador de expresiones CXX0039
símbolo es ambiguo  
  
 El evaluador de expresiones de C no puede determinar qué instancia de un símbolo para usarlo en una expresión. El símbolo se produce más de una vez en el árbol de herencia.  
  
 Debe utilizar el operador de resolución de ámbito (`::`) para especificar explícitamente la instancia a utilizar en la expresión.  
  
 Este error es idéntico a CAN0039.