---
title: 'Cómo: usar un tipo nativo en una compilación de-CLR'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, native types in /clr
- /clr compiler option [C++], using native types
ms.assetid: 3a505c90-4adb-4942-9cf9-7d1fdcbc01e7
ms.openlocfilehash: b506c3d825c4c26236a4ac3fc9682067a011315a
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545208"
---
# <a name="how-to-use-a-native-type-in-a-clr-compilation"></a>Cómo: Utilizar un tipo nativo en una compilación con /clr

Puede definir un tipo nativo en una compilación **/CLR** y cualquier uso de ese tipo nativo desde dentro del ensamblado es válido. Sin embargo, los tipos nativos no estarán disponibles para su uso desde metadatos a los que se hace referencia.

Cada ensamblado debe contener la definición de todos los tipos nativos que utilizará.

Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

Este ejemplo crea un componente que define y utiliza un tipo nativo.

```cpp
// use_native_type_in_clr.cpp
// compile with: /clr /LD
public struct NativeClass {
   static int Test() { return 98; }
};

public ref struct ManagedClass {
   static int i = NativeClass::Test();
   void Test() {
      System::Console::WriteLine(i);
   }
};
```

## <a name="example"></a>Ejemplo

Este ejemplo define un cliente que utiliza el componente. Tenga en cuenta que es un error el acceso al tipo nativo, a menos que esté definido en la compilación.

```cpp
// use_native_type_in_clr_2.cpp
// compile with: /clr
#using "use_native_type_in_clr.dll"
// Uncomment the following 3 lines to resolve.
// public struct NativeClass {
//    static int Test() { return 98; }
// };

int main() {
   ManagedClass x;
   x.Test();

   System::Console::WriteLine(NativeClass::Test());   // C2653
}
```

## <a name="see-also"></a>Consulte también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
