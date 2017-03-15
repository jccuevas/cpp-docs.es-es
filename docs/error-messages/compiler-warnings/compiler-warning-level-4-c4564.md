---
title: "Advertencia del compilador (nivel 4) C4564 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4564"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4564"
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia del compilador (nivel 4) C4564
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el método 'método' de clase 'clase' define un parámetro 'parámetro' predeterminado no compatible  
  
 El compilador detectó un método con uno o varios parámetros con valores predeterminados.  El valor o valores predeterminados de los parámetros se omitirá al invocar el método; especifique valores para esos parámetros de forma explícita.  De no hacerlo, el compilador de C\+\+ generará un error.  
  
 Dado el siguiente archivo .dll creado con Visual Basic, que permite parámetros predeterminados en argumentos de métodos:  
  
```  
' C4564.vb  
' compile with: vbc /t:library C4564.vb  
Public class TestClass  
   Public Sub MyMethod (a as Integer, _  
                        Optional c as Integer=1)  
   End Sub  
End class  
```  
  
 Y el ejemplo siguiente de C\+\+, que utiliza la DLL creada con Visual Basic,  
  
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