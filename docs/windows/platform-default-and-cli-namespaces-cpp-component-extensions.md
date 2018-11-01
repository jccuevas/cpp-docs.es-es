---
title: Plataforma, predeterminado y cli de espacios de nombres (C++ / c++ / CLI y c++ / CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- lang
- cli
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
ms.openlocfilehash: fb7c9135051d790a488775451e1d333ce69d3dda
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598014"
---
# <a name="platform-default-and-cli-namespaces--ccli-and-ccx"></a>Plataforma, predeterminado y cli de espacios de nombres (C++ / c++ / CLI y c++ / CX)

Un espacio de nombres califica los nombres de los elementos de lenguaje de modo que no entren en conflicto con nombres que por lo demás son idénticos en otra parte del código fuente. Por ejemplo, un conflicto de nombres podría evitar que el compilador reconociera [palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md). El compilador utiliza los espacios de nombres, pero no se conservan en el ensamblado compilado.

## <a name="all-runtimes"></a>Todos los runtimes

Visual Studio proporciona un espacio de nombres predeterminado para el proyecto cuando se crea el proyecto. Puede cambiar manualmente el espacio de nombres, aunque en C++ / c++ / CX, el nombre del archivo .winmd debe coincidir con el nombre del espacio de nombres raíz.

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

Para obtener más información, consulte [visibilidad de espacios de nombres y tipos (C++ / c++ / CX)](https://msdn.microsoft.com/library/windows/apps/hh969551.aspx).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="syntax"></a>Sintaxis

```cpp
using namespace cli;
```

### <a name="remarks"></a>Comentarios

C++ / c++ / CLI es compatible con la **cli** espacio de nombres. Cuando se compila con `/clr`, **mediante** instrucción en la sección sintaxis está implícita.

Las siguientes características de lenguaje están en el **cli** espacio de nombres:

- [Matrices](../windows/arrays-cpp-component-extensions.md)

- [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)

- [pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)

- [safe_cast](../windows/safe-cast-cpp-component-extensions.md)

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

En el ejemplo de código siguiente se muestra que es posible usar un símbolo en el **cli** espacio de nombres como un símbolo definido por el usuario en el código.  Sin embargo, una vez que lo ha hecho, deberá calificar explícita o implícitamente las referencias a la **cli** elemento del lenguaje del mismo nombre.

```cpp
// cli_namespace.cpp
// compile with: /clr
using namespace cli;
int main() {
   array<int> ^ MyArray = gcnew array<int>(100);
   int array = 0;

   array<int> ^ MyArray2 = gcnew array<int>(100);   // C2062

   // OK
   cli::array<int> ^ MyArray2 = gcnew cli::array<int>(100);
   ::array<int> ^ MyArray3 = gcnew ::array<int>(100);
}
```

## <a name="see-also"></a>Vea también

[Extensiones de componentes de .NET y UWP](../windows/component-extensions-for-runtime-platforms.md)