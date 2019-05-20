---
title: Procedimiento Declaración de tipos de valor con la palabra clave interior_ptr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- _ptr keyword
- value types, declaring
ms.assetid: 49eea66e-eeba-49bd-95b0-ba297be436e3
ms.openlocfilehash: 2b75f6c4763ddd7d3fd2d802371e21c40d506b16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515760"
---
# <a name="how-to-declare-value-types-with-the-interiorptr-keyword-ccli"></a>Procedimiento Declaración de tipos de valor con la palabra clave interior_ptr (C++/CLI)

Una palabra clave **interior_ptr** puede utilizarse con un tipo de valor.

> [!IMPORTANT]
> Esta característica del lenguaje es compatible con la opción de compilador `/clr`, pero no con la opción de compilador `/ZW`.

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

En el siguiente ejemplo de C++/CLI se muestra cómo usar **interior_ptr** con un tipo de valor.

### <a name="code"></a>Código

```cpp
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

```Output
1
2
2
3
3
3
```

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

En un tipo de valor, el puntero **this** se evalúa como interior_ptr.

En el cuerpo de una función miembro no estática de un tipo de valor `V`, **this** es una expresión de tipo `interior_ptr<V>` cuyo valor es la dirección del objeto para el que se invoca la función.

### <a name="code"></a>Código

```cpp
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

En el ejemplo siguiente se muestra cómo usar la dirección del operador con miembros estáticos.

La dirección de un miembro de tipo Visual C++ estático produce un puntero nativo.  La dirección de un miembro de tipo de valor estático es un puntero administrado porque el miembro de tipo de valor se asigna en el montón de tiempo de ejecución y se puede mover mediante el recolector de elementos no utilizados.

### <a name="code"></a>Código

```cpp
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

```Output
22
23
hello
```

## <a name="see-also"></a>Vea también

[interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)