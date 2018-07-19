---
title: 'Cómo: declarar tipos de valor con la palabra clave interior_ptr (C++ / CLI) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- _ptr keyword
- value types, declaring
ms.assetid: 49eea66e-eeba-49bd-95b0-ba297be436e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6015d5a61589b8ed2d38b6491392fd42e4f38ef1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879482"
---
# <a name="how-to-declare-value-types-with-the-interiorptr-keyword-ccli"></a>Cómo: Declarar tipos de valor con la palabra clave interior_ptr (C++/CLI)
Un `interior_ptr` puede utilizarse con un tipo de valor.  
  
> [!IMPORTANT]
>  Esta característica de lenguaje es compatible con la **/CLR** opción del compilador, pero no en el **/ZW** opción del compilador.  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 El siguiente C++ / CLI muestra cómo utilizar un `interior_ptr` con un tipo de valor.  
  
### <a name="code"></a>Código  
  
```  
// interior_ptr_value_types.cpp  
// compile with: /clr  
value struct V {  
   V(int i) : data(i){}  
   int data;  
};  
  
int main() {  
   V v(1);  
   System::Console::WriteLine(v.data);  
  
   // pointing to a value type  
   interior_ptr<V> pv = &v;  
   pv->data = 2;  
  
   System::Console::WriteLine(v.data);  
   System::Console::WriteLine(pv->data);  
  
   // pointing into a value type  
   interior_ptr<int> pi = &v.data;  
   *pi = 3;  
   System::Console::WriteLine(*pi);  
   System::Console::WriteLine(v.data);  
   System::Console::WriteLine(pv->data);  
}  
```  
  
### <a name="output"></a>Salida  
  
```  
1  
2  
2  
3  
3  
3  
```  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 En un tipo de valor, el `this` se evalúa como puntero en interior_ptr.  
  
 En el cuerpo de una función miembro no estático de un tipo de valor `V`, `this` es una expresión de tipo `interior_ptr<V>` cuyo valor es la dirección del objeto para el que se llama a la función.  
  
### <a name="code"></a>Código  
  
```  
// interior_ptr_value_types_this.cpp  
// compile with: /clr /LD  
value struct V {  
   int data;  
   void f() {  
      interior_ptr<V> pv1 = this;  
      // V* pv2 = this;   error  
   }  
};  
```  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 El ejemplo siguiente muestra cómo utilizar el operador address-of con miembros estáticos.  
  
 La dirección de un miembro de tipo estático de Visual C++ produce un puntero nativo.  La dirección de un miembro de tipo de valor estático es un puntero administrado porque el miembro de tipo de valor se asigna en el montón en tiempo de ejecución y se puede mover por el recolector de elementos no utilizados.  
  
### <a name="code"></a>Código  
  
```  
// interior_ptr_value_static.cpp  
// compile with: /clr  
using namespace System;  
value struct V { int i; };  
  
ref struct G {  
   static V v = {22};   
   static int i = 23;   
   static String^ pS = "hello";   
};  
  
int main() {  
   interior_ptr<int> p1 = &G::v.i;  
   Console::WriteLine(*p1);  
  
   interior_ptr<int> p2 = &G::i;  
   Console::WriteLine(*p2);  
  
   interior_ptr<String^> p3 = &G::pS;  
   Console::WriteLine(*p3);  
}  
```  
  
### <a name="output"></a>Salida  
  
```  
22  
23  
hello  
```  
  
## <a name="see-also"></a>Vea también  
 [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)