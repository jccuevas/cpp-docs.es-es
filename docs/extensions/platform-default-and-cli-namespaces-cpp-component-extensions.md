---
title: Espacios de nombres de plataforma, predeterminado y cli (C++/CLI y C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- lang
- cli
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
ms.openlocfilehash: db6c73d6c52bf97aea5d0fbeeeebdeef87f692cc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544655"
---
# <a name="platform-default-and-cli-namespaces--ccli-and-ccx"></a>Espacios de nombres de plataforma, predeterminado y cli (C++/CLI y C++/CX)

Un espacio de nombres califica los nombres de los elementos de lenguaje de modo que no entren en conflicto con nombres que por lo demás son idénticos en otra parte del código fuente. Por ejemplo, si se produce una colisión de nombres, es posible que el compilador no reconozca las [palabras clave contextuales](context-sensitive-keywords-cpp-component-extensions.md). El compilador utiliza los espacios de nombres, pero no se conservan en el ensamblado compilado.

## <a name="all-runtimes"></a>Todos los runtimes

Visual Studio proporciona un espacio de nombres predeterminado para el proyecto cuando se crea. Puede cambiar manualmente el espacio de nombres, aunque en C++/CX el nombre del archivo .winmd debe coincidir con el del espacio de nombres raíz.

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

Para obtener más información, consulte [Visibilidad de espacios de nombres y tipos (C++/CX)](../cppcx/namespaces-and-type-visibility-c-cx.md).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="syntax"></a>Sintaxis

```cpp
using namespace cli;
```

### <a name="remarks"></a>Observaciones

C++/CLI admite el espacio de nombres **cli**. Al compilar con `/clr`, la instrucción **using** de la sección Sintaxis está implícita.

Las características de lenguaje siguientes están en el espacio de nombres **cli**:

- [Matrices](arrays-cpp-component-extensions.md)

- [interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)

- [pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)

- [safe_cast](safe-cast-cpp-component-extensions.md)

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

En el ejemplo de código siguiente se muestra que se puede usar un símbolo en el espacio de nombres **cli** como símbolo definido por el usuario en el código.  Sin embargo, después de realizar esta acción, deberá calificar explícita o implícitamente las referencias al elemento de lenguaje **cli** del mismo nombre.

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

## <a name="see-also"></a>Consulte también

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)