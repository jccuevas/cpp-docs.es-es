---
title: Compilador advertencia (nivel 1) C4027 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4027
dev_langs:
- C++
helpviewer_keywords:
- C4027
ms.assetid: f30d57b9-20c4-4284-8686-566d9f0ca7fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cbad35c43f602dcaa83f550db887275db3e5213c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4027"></a>Advertencia del compilador (nivel 1) C4027
función declarada sin lista de parámetros formales  
  
 La declaración de función no toma parámetros formales, pero existen parámetros formales en la definición de función o parámetros reales en una llamada. Las llamadas posteriores a esta función suponen que la función toma parámetros reales de los tipos encontrados en la definición de función o la llamada.