---
title: Advertencia de las herramientas del vinculador LNK4227
ms.date: 11/04/2016
f1_keywords:
- LNK4227
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
ms.openlocfilehash: 7b75cff4f03370951245bde1b485d538ffdb4007
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182947"
---
# <a name="linker-tools-warning-lnk4227"></a>Advertencia de las herramientas del vinculador LNK4227

> ADVERTENCIA de operación de metadatos (*HRESULT*): *warning_message*

El enlazador detectó diferencias de metadatos al combinar:

- Uno o varios ensamblados a los que se hace referencia con el ensamblado que se está compilando actualmente.

- Uno o más archivos de código fuente en una compilación.

Por ejemplo, LNK4227 puede producirse si tiene dos funciones globales con el mismo nombre, pero la información de parámetros se ha declarado diferente (es decir, las declaraciones no son coherentes en todos los compilandos). Use Ildasm. exe/TEXT/METADATA *object_file* en cada archivo. obj para ver la diferencia entre los tipos.

LNK4227 también se utiliza para notificar los problemas que se originan con otra herramienta. Busque el mensaje de advertencia para obtener más información.

Los problemas de metadatos deben corregirse para resolver la advertencia.

## <a name="example"></a>Ejemplo

LNK4227 se genera cuando un ensamblado al que se hace referencia se firmó de manera diferente que el ensamblado que hace referencia a él.

En el ejemplo siguiente se genera LNK4227:

```cpp
// LNK4227.cpp
// compile with: /clr
using namespace System::Reflection;

[assembly:AssemblyDelaySignAttribute(false)];

int main() {}
```

y, a continuación,

```cpp
// LNK4227b.cpp
// compile with: /clr LNK4227.cpp /FeLNK4227b.exe
using namespace System::Reflection;
using namespace System::Runtime::CompilerServices;

[assembly:AssemblyDelaySignAttribute(true)];
// Try the following line instead
// [assembly:AssemblyDelaySignAttribute(false)];

ref class MyClass
{
};
```

## <a name="example"></a>Ejemplo

LNK4227 también se puede generar cuando los números de versión con el formato incorrecto se pasan a los atributos de ensamblado.  La notación ' * ' es específica de la `AssemblyVersionAttribute`.  Para resolver esta advertencia, use solo números en los atributos de versión distintos de `AssemblyVersionAttribute`.

En el ejemplo siguiente se genera LNK4227:

```cpp
// LNK4227e.cpp
// compile with: /clr /LD /W1
using namespace System::Reflection;
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227
// try the following line instead
// [assembly:AssemblyFileVersionAttribute("2.3")];
```
