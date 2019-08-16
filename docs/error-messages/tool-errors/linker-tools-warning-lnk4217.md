---
title: Advertencia de las herramientas del vinculador LNK4217
ms.date: 07/23/2019
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: 1301dd53f71c616d7b7af346923a54c42903c9fd
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450860"
---
# <a name="linker-tools-warning-lnk4217"></a>Advertencia de las herramientas del vinculador LNK4217

> el símbolo '*Symbol*' definido en '*filename_1. obj*' es importado por '*filename_2. obj*' en la función '*function*'

[_ _ declspec (dllimport)](../../cpp/dllexport-dllimport.md) se especificó para un símbolo, aunque el símbolo está definido en un archivo objeto de la misma imagen. Quite el `__declspec(dllimport)` modificador para resolver esta advertencia.

## <a name="remarks"></a>Comentarios

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

## <a name="see-also"></a>Vea también

[ADVERTENCIA de las herramientas del vinculador LNK4049](linker-tools-warning-lnk4049.md) \
[ADVERTENCIA de las herramientas del vinculador LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)