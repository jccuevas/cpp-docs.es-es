---
title: C3198 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3198
dev_langs:
- C++
helpviewer_keywords:
- C3198
ms.assetid: ec4ecf61-0067-4aa4-b443-a91013a1e59d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0516e7cae12e544195d157781e6ed86923470420
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250910"
---
# <a name="compiler-error-c3198"></a>C3198 de Error del compilador
uso no válido de pragmas de punto flotante: fenv_access (pragma) funciona solo en el modo preciso  
  
 [fenv_access](../../preprocessor/fenv-access.md) pragma se usó en una [/FP](../../build/reference/fp-specify-floating-point-behavior.md) valor distinto de **/fp: precisa**.  
  
 El ejemplo siguiente genera C3198:  
  
```  
// C3198.cpp  
// compile with: /fp:fast  
#pragma fenv_access(on)   // C3198  
```