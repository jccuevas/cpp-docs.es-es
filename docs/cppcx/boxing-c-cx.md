---
title: Conversión boxing (C++/CX)
ms.date: 12/30/2016
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
ms.openlocfilehash: c680ea0262e8e65345cba40280a389453c2985bb
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519521"
---
# <a name="boxing-ccx"></a>Conversión boxing (C++/CX)

*Boxing* es el ajuste de una variable de tipo de valor como [Windows::Foundation::DateTime](https://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx)(o un tipo escalar fundamental como `int`) en una clase ref cuando la variable se pasa a un método que toma [Platform::Object^](../cppcx/platform-object-class.md) como tipo de entrada.

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

[Sistema de tipos (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Conversión (C++/CX)](../cppcx/casting-c-cx.md)<br/>
[Referencia del lenguaje de Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)