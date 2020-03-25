---
title: Advertencia de las herramientas del vinculador LNK4049
ms.date: 04/15/2019
f1_keywords:
- LNK4049
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
ms.openlocfilehash: a8e4416eafd47f584de4ab1c83aa7303cab0440a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194140"
---
# <a name="linker-tools-warning-lnk4049"></a>Advertencia de las herramientas del vinculador LNK4049

> se importó el símbolo '*Symbol*' definido en '*filename. obj*'

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) se especificó para *Symbol* , aunque el símbolo se haya definido en el archivo de objeto *filename. obj* en la misma imagen. Quite el modificador `__declspec(dllimport)` para resolver esta advertencia.

## <a name="remarks"></a>Observaciones

El enlazador genera esta advertencia cuando se define un símbolo en un archivo objeto y se hace referencia a él mediante el modificador de la declaración de `__declspec(dllimport)` en otro.

Warning LNK4049 es una versión más general de la [Advertencia de las herramientas del vinculador LNK4217](linker-tools-warning-lnk4217.md). El enlazador genera LNK4049 de advertencia cuando no puede determinar qué función o archivo objeto hacía referencia al símbolo importado.

Los casos comunes en los que se genera LNK4049 en lugar de LNK4217 son:

- Cuando se usa la opción [/incremental](../../build/reference/incremental-link-incrementally.md) .

- Cuando se usa la opción [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) .

Para resolver LNK4049, pruebe uno de los procedimientos siguientes:

- Quite el modificador `__declspec(dllimport)` de la declaración adelantada del símbolo que desencadenó LNK4049. Puede buscar símbolos en una imagen binaria mediante la utilidad **dumpbin** . El conmutador **dumpbin/Symbols** muestra la tabla de símbolos COFF de la imagen. Para obtener más información sobre la utilidad **dumpbin** , vea [referencia de DUMPBIN](../../build/reference/dumpbin-reference.md).

- Deshabilite temporalmente la vinculación incremental y la optimización de todo el programa. Cuando se vuelve a compilar, la aplicación genera LNK4217 de advertencia, que incluye el nombre de la función que hace referencia al símbolo importado. Quite el modificador de declaración `__declspec(dllimport)` del símbolo importado y vuelva a habilitar la vinculación incremental o la optimización de todo el programa según sea necesario.

Aunque el código generado final se comporta correctamente, el código generado para llamar a la función importada es menos eficaz que llamar directamente a la función. Esta advertencia no aparece cuando se compila con la opción [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) .

Para obtener más información sobre las declaraciones de datos de importación y exportación, vea [dllexport, DllImport](../../cpp/dllexport-dllimport.md).

## <a name="example"></a>Ejemplo

La vinculación de los dos módulos siguientes generará LNK4049. El primer módulo genera un archivo objeto que contiene una función exportada única.

```cpp
// LNK4049a.cpp
// compile with: /c

__declspec(dllexport) int func()
{
   return 3;
}
```

El segundo módulo genera un archivo objeto que contiene una declaración adelantada a la función exportada en el primer módulo, junto con una llamada a esta función dentro de la función `main`. Al vincular este módulo con el primer módulo, se generará LNK4049. Quite el modificador `__declspec(dllimport)` de la declaración para resolver la advertencia.

```cpp
// LNK4049b.cpp
// compile with: /link /WX /LTCG LNK4049a.obj
// LNK4049 expected

__declspec(dllimport) int func();
// try the following line instead
// int func();

int main()
{
   return func();
}
```

## <a name="see-also"></a>Consulte también

[Advertencia de las herramientas del vinculador LNK4217](linker-tools-warning-lnk4217.md) \
[Advertencia de las herramientas del vinculador LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)
