---
title: Error irrecuperable C1103 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1103
dev_langs: C++
helpviewer_keywords: C1103
ms.assetid: 9d276939-9c47-4235-9d20-76b8434f9731
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f35bcec3b89e8e6c95740d1efb2dbbe98851f1a8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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