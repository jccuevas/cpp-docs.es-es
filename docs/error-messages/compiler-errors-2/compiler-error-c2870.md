---
title: Error del compilador C2870 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2870
dev_langs:
- C++
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5fe9f47a96422493d6d731a18add8c23ff683f14
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33243494"
---
# <a name="compiler-error-c2870"></a>Error del compilador C2870
'name': una definición de espacio de nombres debe aparecer en el ámbito de archivo o directamente dentro de otra definición de espacio de nombres  
  
 Define el espacio de nombres `name` incorrectamente. Espacios de nombres se deben definir en el ámbito de archivo (fuera de todos los bloques y clases) o se encuentran en otro espacio de nombres.  
  
 El ejemplo siguiente genera C2870:  
  
```  
// C2870.cpp  
// compile with: /c  
int main() {  
   namespace A { int i; };   // C2870  
}  
```