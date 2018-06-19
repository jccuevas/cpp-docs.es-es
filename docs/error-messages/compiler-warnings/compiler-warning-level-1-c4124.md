---
title: Compilador advertencia (nivel 1) C4124 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4124
dev_langs:
- C++
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: accd58c123bcd74e54176eed5eb974c3df33dbab
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279323"
---
# <a name="compiler-warning-level-1-c4124"></a>Compilador advertencia (nivel 1) C4124
__fastcall con comprobación de pila es ineficaz  
  
 El `__fastcall` palabra clave se usó con comprobación de pila habilitada.  
  
 El `__fastcall` convención genera código más rápido, pero la comprobación de pila hace el código más lento. Cuando se usa `__fastcall`, desactive la opción de comprobación de la pila con la **check_stack** pragma o/GS.  
  
 Esta advertencia se emite solo para la primera función declarada en estas condiciones.