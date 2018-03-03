---
title: Compilador advertencia (nivel 4) C4710 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4710
dev_langs:
- C++
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0464d924c21a029a97a8f03d30f88127f3aea6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4710"></a>Advertencia del compilador (nivel 4) C4710
'función': función no está entre línea  
  
 La función especificada se seleccionaron para la expansión en línea, pero el compilador no realizó la inserción.  
  
 Inserción se realiza a discreción del compilador. El **en línea** palabra clave, como el **registrar** palabra clave, se utiliza como una sugerencia para el compilador. El compilador utiliza la heurística para determinar si debe incluir en línea una determinada función para acelerar el código cuando se compila para acelerar el proceso, o si debe incluir en línea una determinada función para hacer que el código de menor cuando se compila con espacio. El compilador incluirá solo muy pequeñas funciones cuando se compila con espacio.  
  
 En algunos casos, el compilador no insertará una determinada función por motivos mecánicos. Vea [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) para obtener una lista de motivos por los que el compilador no alinear una función.  
  
 De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.