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
ms.openlocfilehash: a7599e2987d27626e6f5c9d049d9a3bd4509c3ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516520"
---
# <a name="platform-default-and-cli-namespaces--ccli-and-ccx"></a>Espacios de nombres de plataforma, predeterminado y cli (C++/CLI y C++/CX)

Un espacio de nombres califica los nombres de los elementos de lenguaje de modo que no entren en conflicto con nombres que por lo demás son idénticos en otra parte del código fuente. Por ejemplo, si se produce una colisión de nombres, es posible que el compilador no reconozca las [palabras clave contextuales](context-sensitive-keywords-cpp-component-extensions.md). El compilador utiliza los espacios de nombres, pero no se conservan en el ensamblado compilado.

## <a name="all-runtimes"></a>Todos los runtimes

Visual Studio proporciona un espacio de nombres predeterminado para el proyecto cuando se crea. Puede cambiar manualmente el espacio de nombres, aunque en C++/CX el nombre del archivo .winmd debe coincidir con el del espacio de nombres raíz.

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

Para obtener más información, consulte [Visibilidad de espacios de nombres y tipos (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh969551.aspx).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="syntax"></a>Sintaxis

```cpp
using namespace cli;
```

### <a name="remarks"></a>Comentarios

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

## <a name="see-also"></a>Vea también

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)