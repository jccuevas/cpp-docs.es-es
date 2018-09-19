---
title: Las herramientas del vinculador LNK4227 advertencia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4227
dev_langs:
- C++
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28bcf242e48046278030ec4259b7ae3edd1c4a61
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088870"
---
# <a name="linker-tools-warning-lnk4227"></a>Advertencia de las herramientas del vinculador LNK4227

> Advertencia de operación de metadatos (*HRESULT*): *mensaje_de_advertencia*

El vinculador detectó diferencias de metadatos al fusionar mediante combinación:

- Uno o más ensamblados que se hace referencia con el ensamblado que se está compilando actualmente.

- Uno o varios archivos de código fuente una compilación.

Por ejemplo, puede deberse LNK4227 si tiene dos funciones globales con el mismo nombre pero con información de parámetros que se declaran de forma diferente (es decir, las declaraciones no son coherentes en todos los elementos). Use ildasm.exe /TEXT /METADATA *las diferencias entre* en cada archivo .obj para ver cómo difieren los tipos.

LNK4227 también se usa para informar sobre los problemas que se originan con otra herramienta. Busque el mensaje de advertencia para obtener más información.

Para resolver la advertencia, se deben corregir los problemas de los metadatos.

## <a name="example"></a>Ejemplo

LNK4227 se genera cuando un ensamblado de referencia estaba firmado de manera diferente que el ensamblado que hace referencia a él.

El ejemplo siguiente genera la advertencia LNK4227:

```cpp
// LNK4227.cpp
// compile with: /clr
using namespace System::Reflection;

[assembly:AssemblyDelaySignAttribute(false)];

int main() {}
```

Y entonces

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

También se puede generar LNK4227 cuando se pasan los números de versión en un formato incorrecto para los atributos de ensamblado.  El ' *' notación es específica de la `AssemblyVersionAttribute`.  Para resolver esta advertencia, use solo números en los atributos de versión distinto `AssemblyVersionAttribute`.

El ejemplo siguiente genera la advertencia LNK4227:

```cpp
// LNK4227e.cpp
// compile with: /clr /LD /W1
using namespace System::Reflection;
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227
// try the following line instead
// [assembly:AssemblyFileVersionAttribute("2.3")];
```