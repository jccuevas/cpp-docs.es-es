---
title: Compilador advertencia (nivel 2) C4099 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4099
dev_langs:
- C++
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 855b31903ba36f6c1ab3030e91354175441451a9
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-2-c4099"></a>Compilador advertencia (nivel 2) C4099
'identificador': nombre de tipo visto anteriormente usando 'tipodeobjeto1' ahora se ve usando 'tipodeobjeto2'  
  
 Un objeto declarado como una estructura se define como una clase o un objeto declarado como una clase se define como una estructura. El compilador utiliza el tipo especificado en la definición.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente genera el error C4099.  
  
```  
// C4099.cpp  
// compile with: /W2 /c  
struct A;  
class A {};   // C4099, use different identifer or use same object type  
```
