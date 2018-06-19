---
title: Compilador advertencia (nivel 1) C4488 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4488
dev_langs:
- C++
helpviewer_keywords:
- C4488
ms.assetid: 55625e46-ddb5-4c7c-99c7-cd4aa9f879bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a3c5fc64637d989066acfa90715c50504664231
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281527"
---
# <a name="compiler-warning-level-1-c4488"></a>Advertencia del compilador (nivel 1) C4488
'función': requiere la palabra clave 'palabra clave' para implementar el método de interfaz 'método_de_interfaz'  
  
 Una clase debe implementar todos los miembros de una interfaz de la que hereda directamente. Un miembro implementado debe tener accesibilidad pública y debe marcarse como virtual.  
  
## <a name="example"></a>Ejemplo  
 Puede producirse la advertencia C4488 si un miembro implementado no es público. El ejemplo siguiente genera la advertencia C4488.  
  
```  
// C4488.cpp  
// compile with: /clr /c /W1 /WX  
interface struct MyI {  
   void f1();  
};  
  
// implemented member not public  
ref class B : MyI { virtual void f1() {} };  // C4488  
  
// OK  
ref class C : MyI {  
public:  
   virtual void f1() {}  
};  
```  
  
## <a name="example"></a>Ejemplo  
 Puede producirse la advertencia C4488 si un miembro implementado no está marcado como virtual. El ejemplo siguiente genera la advertencia C4488.  
  
```  
// C4488_b.cpp  
// compile with: /clr /c /W1 /WX  
interface struct MyI {  
   void f1();  
};  
  
ref struct B : MyI { void f1() {} };   // C4488  
ref struct C : MyI { virtual void f1() {} };   // OK  
```