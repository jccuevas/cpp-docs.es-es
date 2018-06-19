---
title: Compilador advertencia (nivel 1) C4096 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4096
dev_langs:
- C++
helpviewer_keywords:
- C4096
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3787ef5482841e33658e02371fa0f6d1682612ac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276284"
---
# <a name="compiler-warning-level-1-c4096"></a>Compilador advertencia (nivel 1) C4096
'a': interfaz no es una interfaz COM; no se emitirá para IDL  
  
 Una definición de interfaz que realmente como una interfaz COM no se ha definido como una interfaz COM y, por tanto, no se emitirá para el archivo IDL.  
  
 Vea [atributos de la interfaz](../../windows/interface-attributes.md) para una lista de atributos que indican una interfaz es una interfaz COM.  
  
 El ejemplo siguiente genera C4096:  
  
```  
// C4096.cpp  
// compile with: /W1 /LD  
#include "windows.h"  
[module(name="xx")];  
  
// [object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface a  
{  
};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000002")]  
struct b : a  
{  
};   // C4096, remove coclass or uncomment object  
```