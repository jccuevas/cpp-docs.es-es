---
title: Compilador advertencia (nivel 1) C4445 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4445
dev_langs:
- C++
helpviewer_keywords:
- C4445
ms.assetid: 535e92a0-ba08-4dfc-89b2-af2dcdd7caeb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: abd0d15113373f752bb861d73e48091687b2f0d2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4445"></a>Advertencia del compilador (nivel 1) C4445
'función': un método virtual no puede ser privado en un tipo WinRT o administrado  
  
 Si una función virtual es privada, un tipo derivado no puede tener acceso a ella. Para corregir este error, cambie la accesibilidad de la función miembro virtual a protegida o pública.