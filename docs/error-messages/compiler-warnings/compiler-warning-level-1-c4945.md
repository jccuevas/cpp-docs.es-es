---
title: Error de compilador advertencia (nivel 1) C4945 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4945
dev_langs:
- C++
helpviewer_keywords:
- C4945
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
caps.latest.revision: 8
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
ms.openlocfilehash: 04cd425a7e285fe3610604a76a2e61958051b101
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4945"></a>Advertencia del compilador (nivel 1) C4945
'símbolo': no se puede importar un símbolo desde 'ensamblado2': como 'símbolo' ya se ha importado desde otro ensamblado 'ensamblado1'  
  
 Se importó un símbolo desde un ensamblado de referencia, pero ese símbolo ya se importó desde otro ensamblado referenciado. No hacer referencia a uno de los ensamblados u obtener el nombre del símbolo cambiado en uno de los ensamblados.  
  
 Los ejemplos siguientes generan el error C4945.  
  
```  
// C4945a.cs  
// compile with: /target:library  
// C# source code to create a dll  
public class ClassA {  
   public int i;  
}  
```  
  
 Y entonces  
  
```  
// C4945b.cs  
// compile with: /target:library  
// C# source code to create a dll  
public class ClassA {  
   public int i;  
}  
```  
  
 Y entonces  
  
```  
// C4945c.cpp  
// compile with: /clr /LD /W1  
#using "C4945a.dll"  
#using "C4945b.dll"   // C4945  
```
