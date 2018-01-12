---
title: Error del compilador C3104 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3104
dev_langs: C++
helpviewer_keywords: C3104
ms.assetid: b5648d47-e5d3-4b45-a3c0-f46e04eae731
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b23007d4985319a7570b9efb4a0f14f639a0c0d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3104"></a>Error del compilador C3104
argumento de atributo no válido  
  
 Ha especificado un argumento no válido a un atributo.  
  
 Vea [tipos de parámetro de atributo](../../windows/attribute-parameter-types-cpp-component-extensions.md) para obtener más información.  
  
 Este error puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual C++ 2005: cuando se pasan matrices administradas a atributos personalizados, el tipo de la matriz ya no se deduce de la lista de inicialización de agregado. Ahora, el compilador requiere especificar el tipo de la matriz, así como la lista de inicializadores.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3104.  
  
```  
// C3104a.cpp  
// compile with: /clr /c  
using namespace System;  
  
[AttributeUsage(AttributeTargets::Class)]  
public ref struct ABC : public Attribute {  
   ABC(array<int>^){}  
   array<double> ^ param;  
};  
  
[ABC( {1,2,3}, param = {2.71, 3.14})]   // C3104  
// try the following line instead  
// [ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]   
ref struct AStruct{};  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3104.  
  
```  
// C3104b.cpp  
// compile with: /clr /c  
// C3104 expected  
using namespace System;  
  
int func() {  
   return 0;   
}  
  
[attribute(All)]  
ref class A {  
public:   
   A(int) {}  
};  
  
// Delete the following 2 lines to resolve.  
[A(func())]  
ref class B {};  
  
// OK  
[A(0)]  
ref class B {};  
```  
