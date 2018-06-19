---
title: Compilador advertencia (nivel 1) C4025 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4025
dev_langs:
- C++
helpviewer_keywords:
- C4025
ms.assetid: c4f6a651-0641-4446-973e-8290065e49ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47e84ba11c7bed7420a9a1c699361612ef2002d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273954"
---
# <a name="compiler-warning-level-1-c4025"></a>Advertencia del compilador (nivel 1) C4025
'number': el puntero de tipo basado se pasó a la función con los argumentos de variable: parámetro número  
  
 Si se pasa un puntero de tipo basado a una función con argumentos de variable, el puntero se normaliza, con resultados imprevisibles. No pase punteros de tipo basado a funciones con argumentos de variable.