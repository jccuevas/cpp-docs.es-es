---
title: Error irrecuperable C1103 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1103
dev_langs:
- C++
helpviewer_keywords:
- C1103
ms.assetid: 9d276939-9c47-4235-9d20-76b8434f9731
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19f991fd7449eda11651dcca4adc73190e276e35
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226080"
---
# <a name="fatal-error-c1103"></a>Error irrecuperable C1103
error irrecuperable al importar el id. de programa: 'mensaje'  
  
 El compilador detectó un problema al importar una biblioteca de tipos.  Por ejemplo, no se puede especificar una biblioteca de tipos con id. de programa y también `no_registry`.  
  
 Para obtener más información, consulte [#import (directiva)](../../preprocessor/hash-import-directive-cpp.md).  
  
 El ejemplo siguiente genera el error C1103:  
  
```  
// C1103.cpp  
#import "progid:a.b.id.1.5" no_registry auto_search   // C1103  
```