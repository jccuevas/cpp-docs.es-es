---
title: Compilador advertencia (nivel 4) C4564 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4564
dev_langs:
- C++
helpviewer_keywords:
- C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f0cf68eb75d420a0d23c04687d4f9492910b53f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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