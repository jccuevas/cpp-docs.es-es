---
title: 'Filtrar Utilice un tipo nativo en una compilación de clr:'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, native types in /clr
- /clr compiler option [C++], using native types
ms.assetid: 3a505c90-4adb-4942-9cf9-7d1fdcbc01e7
ms.openlocfilehash: 9979113ac4ffc062ddfe8654279af03036984f38
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746037"
---
# <a name="how-to-use-a-native-type-in-a-clr-compilation"></a>Procedimiento Usar un tipo nativo en una compilación con /clr

Puede definir un tipo nativo en un **/CLR** compilación y cualquier uso de ese tipo nativo desde dentro del ensamblado es válido. Sin embargo, los tipos nativos no estará disponibles para su uso de los metadatos que se hace referencia.

Cada ensamblado debe contener la definición de cada tipo nativo que se va a utilizar.

Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

Este ejemplo crea un componente que define y utiliza un tipo nativo.

```
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

Este ejemplo define a un cliente que utiliza el componente. Tenga en cuenta que es un error al tener acceso al tipo nativo, a menos que se define en la operación de compilación.

```
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

## <a name="see-also"></a>Vea también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
