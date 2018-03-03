---
title: Compilador advertencia (nivel 4) C4564 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4564
dev_langs:
- C++
helpviewer_keywords:
- C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 25f9f8755acafd71a9ac75a68f601660b781746a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4564"></a>Advertencia del compilador (nivel 4) C4564
el método 'método' de clase 'class' define de forma predeterminada no admitido ' parámetro '  
  
 El compilador detectó un método con uno o varios parámetros con valores predeterminados. Se pasará por alto los valores predeterminados para los parámetros cuando se invoca el método; especificar explícitamente los valores para esos parámetros. Si no especifica valores para esos parámetros explícitamente, el compilador de C++ generará un error.  
  
 Dado el siguiente archivo .dll creado con Visual Basic, que permite parámetros predeterminados en argumentos de método:  
  
```  
' C4564.vb  
' compile with: vbc /t:library C4564.vb  
Public class TestClass  
   Public Sub MyMethod (a as Integer, _  
                        Optional c as Integer=1)  
   End Sub  
End class  
```  
  
 El siguiente ejemplo de C++ que utiliza la DLL creada con Visual Basic, y  
  
```  
// C4564.cpp  
// compile with: /clr /W4 /WX  
#using <C4564.dll>  
  
int main() {  
   TestClass ^ myx = gcnew TestClass();   // C4564  
   myx->MyMethod(9);  
   // try the following line instead, to avoid an error  
   // myx->MyMethod(9, 1);  
}  
```