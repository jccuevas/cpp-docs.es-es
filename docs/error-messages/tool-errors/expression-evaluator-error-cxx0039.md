---
title: Error del evaluador de expresiones CXX0039 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0039
dev_langs: C++
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6edef73f821030f8e8163c10b66efb64649e002f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0039"></a>Error del evaluador de expresiones CXX0039
símbolo es ambiguo  
  
 El evaluador de expresiones de C no puede determinar qué instancia de un símbolo para usarlo en una expresión. El símbolo se produce más de una vez en el árbol de herencia.  
  
 Debe utilizar el operador de resolución de ámbito (`::`) para especificar explícitamente la instancia a utilizar en la expresión.  
  
 Este error es idéntico a CAN0039.