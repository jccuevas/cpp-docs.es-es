---
title: Compilador advertencia (nivel 1) C4944 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4944
dev_langs:
- C++
helpviewer_keywords:
- C4944
ms.assetid: e2905eb1-2e3b-4fab-a48b-c0cae0fd997f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 425a72b75f1ad057a4a09ed11d4dfcfb4acfcb72
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4944"></a>Advertencia del compilador (nivel 1) C4944
'symbol': no se puede importar un símbolo desde 'assembly1': ya que 'symbol' ya existe en el ámbito actual.  
  
 Se definió un símbolo en un archivo de código fuente y, a continuación, una instrucción #using hizo referencia a un ensamblado que también define el símbolo. Se ha ignorado el símbolo en el ensamblado.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea un componente con un tipo llamado ClassA.  
  
```  
// C4944.cs  
// compile with: /target:library  
// C# source code to create a dll  
public class ClassA {  
   public int i;  
}  
```  
  
## <a name="example"></a>Ejemplo  
 Los ejemplos siguientes generan C4944.  
  
```  
// C4944b.cpp  
// compile with: /clr /W1  
class ClassA {  
public:  
   int u;  
};  
  
#using "C4944.dll"   // C4944 ClassA also defined C4944.dll  
  
int main() {  
   ClassA * x = new ClassA();  
   x->u = 9;  
   System::Console::WriteLine(x->u);  
}  
```