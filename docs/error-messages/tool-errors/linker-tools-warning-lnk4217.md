---
title: Advertencia de las herramientas del vinculador LNK4217
ms.date: 07/23/2019
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: 1ce410312493b353bb68ea7264fce9cd6a394e0d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183116"
---
# <a name="linker-tools-warning-lnk4217"></a>Advertencia de las herramientas del vinculador LNK4217

> '*filename_2. obj*' de la función '*function*' importa el símbolo '*symbol*' definido en '*filename_1. obj*'

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) se especificó para un símbolo, aunque el símbolo esté definido en un archivo objeto de la misma imagen. Quite el modificador `__declspec(dllimport)` para resolver esta advertencia.

## <a name="remarks"></a>Observaciones

*Symbol* es el nombre del símbolo que se define dentro de la imagen. *función* es la función que importa el símbolo.

Esta advertencia no aparece cuando se compila con la opción [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) .

LNK4217 también puede producirse si intenta vincular dos módulos juntos, en lugar de ello, debe compilar el segundo módulo con la biblioteca de importación del primer módulo.

```cpp
// main.cpp
__declspec(dllimport) void func();

int main()
{
    func();
    return 0;
}

```

Y luego,

```cpp
// tt.cpp
// compile with: /c
void func() {}
```

Si intenta compilar estos dos módulos, como se muestra aquí, se generará LNK4217:

```cmd
cl.exe /c main.cpp tt.cpp
link.exe main.obj tt.obj
```

Para corregir el error, después de compilar los dos archivos, pase TT. obj a lib. exe para crear un archivo. lib y, a continuación, vincule Main. obj con TT. lib como se muestra aquí:

```cmd
cl.exe /c main.cpp tt.cpp
lib.exe tt.obj /export:func /def
link.exe main.obj tt.lib
```

## <a name="see-also"></a>Consulte también

[Advertencia de las herramientas del vinculador LNK4049](linker-tools-warning-lnk4049.md) \
[Advertencia de las herramientas del vinculador LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)
