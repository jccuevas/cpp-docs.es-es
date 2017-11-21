---
title: "Advertencia de línea de comandos D9043 | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: D9043
dev_langs: C++
helpviewer_keywords: D9043
ms.assetid: 9263e28d-217b-414c-bfb6-86efd3c27a77
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 88e38b333ab28ec15a567d813f09201fd9218060
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="command-line-warning-d9043"></a>Advertencia de la línea de comandos D9043
valor no válido 'nivel_advertencia' para 'compiler_option'; se supone '4999'; Advertencias de análisis de código no están asociadas con niveles de advertencia  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C9043.  
  
```  
// D9043.cpp  
// compile with: /analyze /w16001  
// D9043 warning expected  
int main() {}  
```