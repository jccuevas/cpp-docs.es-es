---
title: Error del compilador C2447 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2447
dev_langs:
- C++
helpviewer_keywords:
- C2447
ms.assetid: d1bd6e9a-ee42-4510-ae5e-6b0378f7b931
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2f0f72bc1278792853e1886e302f4410fdbe2d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197044"
---
# <a name="compiler-error-c2447"></a>Error del compilador C2447
'{': falta el encabezado de función (¿lista formal de estilo anterior?)  
  
 El compilador encontró una llave de apertura inesperada en el ámbito global. En la mayoría de los casos, la causa está en un encabezado de función que tiene un formato incorrecto, una declaración mal colocada o carácter de punto y coma desubicado. Para resolver este problema, compruebe que la llave de apertura va detrás de un encabezado con formato correcto y no va precedida de una declaración o un carácter de punto y coma desubicado.  
  
 Este error también puede deberse a una lista de argumentos formales del lenguaje C de estilo anterior. Para resolver este problema, refactorice la lista de argumentos para que utilice un estilo moderno; es decir, que vaya entre paréntesis.  
  
 El ejemplo siguiente genera C2447:  
  
```  
// C2447.cpp  
int c;  
{}       // C2447  
```