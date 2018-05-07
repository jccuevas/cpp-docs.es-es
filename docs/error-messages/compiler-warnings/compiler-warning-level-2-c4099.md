---
title: Compilador advertencia (nivel 2) C4099 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4099
dev_langs:
- C++
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: afecb3fb2420d27bedf16c81894f224a1119a67b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-2-c4099"></a>Compilador advertencia (nivel 2) C4099
'identificador': nombre de tipo visto anteriormente usando 'tipodeobjeto1' ahora se ve usando 'objecttype2'  
  
 Un objeto declarado como una estructura se define como una clase o un objeto declarado como una clase se define como una estructura. El compilador utiliza el tipo especificado en la definición.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error C4099.  
  
```  
// C4099.cpp  
// compile with: /W2 /c  
struct A;  
class A {};   // C4099, use different identifer or use same object type  
```