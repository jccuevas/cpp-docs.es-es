---
title: Conversión boxing (C++ / c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e70b908bddbf7034e1d60f16cb0e492c0a707586
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598885"
---
# <a name="boxing-ccx"></a>Conversión boxing (C++/CX)
*Boxing* es el ajuste de una variable de tipo de valor como [Windows::Foundation::DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx)(o un tipo escalar fundamental como `int`) en una clase ref cuando la variable se pasa a un método que toma [Platform::Object^](../cppcx/platform-object-class.md) como tipo de entrada.  
  
## <a name="passing-a-value-type-to-an-object-parameter"></a>Pasar un tipo de valor a un parámetro de tipo Object^  
 Aunque no tengas que aplicar conversión boxing de forma explícita a una variable para pasarla a un parámetro de método de tipo [Platform::Object^](../cppcx/platform-object-class.md), tienes que volver a convertir de forma explícita al tipo original cuando recuperes valores a los que se ha aplicado conversión boxing previamente.  
  
 [!code-cpp[cx_boxing#01](../cppcx/codesnippet/CPP/cx_boxing/class1.cpp#01)]  
  
### <a name="using-platformiboxt-to-support-nullable-value-types"></a>Usar Platform:: ibox\<T > para admitir tipos de valor que aceptan valores null  
 C# y Visual Basic admiten el concepto de tipos de valor que aceptan valores NULL. En C / c++ / CX, puede usar el `Platform::IBox<T>` tipo para exponer métodos públicos que admiten parámetros de tipo de valor que acepta valores NULL. El ejemplo siguiente muestra C + + / método público de CX que devuelve null cuando un llamador de C# pasa null para uno de los argumentos.  
  
 [!code-cpp[cx_boxing#02](../cppcx/codesnippet/CPP/cx_boxing/class1.h#02)]  
  
 En un cliente XAML de C#, puedes usarlo de este modo:  
  
```  
  
// C# client code  
    BoxingDemo.Class1 obj = new BoxingDemo.Class1();  
    int? a = null;  
    int? b = 5;  
    var result = obj.Multiply(a,b); //result = null  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Sistema de tipos (C++/CX)](../cppcx/type-system-c-cx.md)   
 [Conversión (C++ / c++ / CX)](../cppcx/casting-c-cx.md)   
 [Referencia del lenguaje de Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)