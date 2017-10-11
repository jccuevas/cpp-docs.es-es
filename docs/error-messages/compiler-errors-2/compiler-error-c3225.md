---
title: Error del compilador C3225 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3225
dev_langs:
- C++
helpviewer_keywords:
- C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 4cf62ba7b0c3b95f22c27172546ccdd253ed9279
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3225"></a>Error del compilador C3225
argumento de tipo genérico para 'arg' no puede ser 'tipo', debe ser un tipo de valor o tipo de identificador  
  
 El argumento de tipo genérico no era del tipo correcto.  
  
 Para obtener más información, consulte [Genéricos](../../windows/generics-cpp-component-extensions.md).  
  
## <a name="example"></a>Ejemplo  
 No se puede crear una instancia de un tipo genérico con un tipo nativo. El ejemplo siguiente genera C3225.  
  
```  
// C3225.cpp  
// compile with: /clr  
class A {};  
  
ref class B {};  
  
generic <class T>  
ref class C {};  
  
int main() {  
   C<A>^ c = gcnew C<A>;   // C3225  
   C<B^>^ c2 = gcnew C<B^>;   // OK  
}  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente crea un componente utilizando C#. Tenga en cuenta que la restricción especifica que sólo se puede crear instancias de tipo genérico con un tipo de valor.  
  
```  
// C3225_b.cs  
// compile with: /target:library  
// a C# program  
public class MyList<T> where T: struct {}  
```  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo utiliza el C#-componente creado e infringe la restricción de que sólo puede ser MyList crea una instancia con un tipo de valor distinto de <xref:System.Nullable>. El ejemplo siguiente genera C3225.  
  
```  
// C3225_c.cpp  
// compile with: /clr  
#using "C3225_b.dll"  
ref class A {};  
value class B {};  
int main() {  
   MyList<A> x;   // C3225  
   MyList<B> y;   // OK  
}  
```
