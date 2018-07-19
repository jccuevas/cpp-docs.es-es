---
title: Compilador advertencia (nivel 4) C4710 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4710
dev_langs:
- C++
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c1cc77d8ee5393fe600ceadd9c1335d76e32efe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296392"
---
# <a name="compiler-warning-level-4-c4710"></a>Advertencia del compilador (nivel 4) C4710
'función': función no está entre línea  
  
 La función especificada se seleccionaron para la expansión en línea, pero el compilador no realizó la inserción.  
  
 Inserción se realiza a discreción del compilador. El **en línea** palabra clave, como el **registrar** palabra clave, se utiliza como una sugerencia para el compilador. El compilador utiliza la heurística para determinar si debe incluir en línea una determinada función para acelerar el código cuando se compila para acelerar el proceso, o si debe incluir en línea una determinada función para hacer que el código de menor cuando se compila con espacio. El compilador incluirá solo muy pequeñas funciones cuando se compila con espacio.  
  
 En algunos casos, el compilador no insertará una determinada función por motivos mecánicos. Vea [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) para obtener una lista de motivos por los que el compilador no alinear una función.  
  
 De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.