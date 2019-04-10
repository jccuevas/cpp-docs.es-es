---
title: Advertencia de las herramientas del vinculador LNK4049
ms.date: 04/09/2019
f1_keywords:
- LNK4049
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
ms.openlocfilehash: 357bf5a981dddadfd79d2d6981ccc9c478909097
ms.sourcegitcommit: 0ad3f4517e64900a2702dd3d366586f9e2bce2c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/10/2019
ms.locfileid: "59477358"
---
# <a name="linker-tools-warning-lnk4049"></a>Advertencia de las herramientas del vinculador LNK4049

> símbolo '*símbolo*'definido en'*nombreDeArchivo.obj*' se importa

El símbolo se ha exportado desde tanto importado al programa.

Esta advertencia se genera el vinculador al definir un símbolo en el archivo de un objeto y hacer referencia a él mediante el uso de la `__declspec(dllimport)` modificador de declaración en otro.

Advertencia LNK4049 es una versión más general de [advertencia de las herramientas del vinculador LNK4217](linker-tools-warning-lnk4217.md). El vinculador genera la advertencia LNK4049 cuando no se puede determinar qué archivo de objeto o función al que hace referencia al símbolo importado.

Los casos más comunes donde LNK4049 se genera en lugar de LNK4217 son:

- Cuando se usa el [incremental](../../build/reference/incremental-link-incrementally.md) opción.

- Cuando se usa el [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) opción.

Para resolver LNK4049, pruebe uno de los procedimientos siguientes:

- Quitar el `__declspec(dllimport)` modificador de la declaración del símbolo que desencadenó LNK4049 hacia delante. Puede buscar símbolos dentro de una imagen binaria mediante el **DUMPBIN** utilidad. El **DUMPBIN /SYMBOLS** modificador muestra la tabla de símbolos COFF de la imagen. Para obtener más información sobre la **DUMPBIN** utilidad, vea [referencia de DUMPBIN](../../build/reference/dumpbin-reference.md).

- Deshabilitar temporalmente la optimización de todo el programa y vinculación incremental. Cuando vuelve a compilar, la aplicación genera la advertencia LNK4217, que incluye el nombre de la función que hace referencia a símbolo importado. Quitar el `__declspec(dllimport)` modificador declaración desde el símbolo importado y volver a habilitar vinculación incremental o la optimización de todo el programa según sea necesario.

Aunque el código generado final se comporta correctamente, el código generado para llamar a la función importada es menos eficaz que llamar directamente a la función. Esta advertencia no aparece cuando se compila con la [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) opción.

Para obtener más información en Importar y exportar las declaraciones de datos, vea [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

## <a name="example"></a>Ejemplo

Vincular los dos módulos siguientes, se generará LNK4049. El primer módulo genera un archivo de objeto que contiene una única función exportada.

```cpp
// LNK4049a.cpp
// compile with: /c

__declspec(dllexport) int func()
{
   return 3;
}
```

El segundo módulo genera un archivo de objeto que contiene una declaración adelantada a la función exportada en el primer módulo, junto con una llamada a esta función dentro de la `main` función. Vincular este módulo con el primer módulo generará LNK4049. Quitar el `__declspec(dllimport)` modificador de la declaración para resolver la advertencia.

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

## <a name="see-also"></a>Vea también

[Herramientas del vinculador LNK4217 de advertencia](linker-tools-warning-lnk4217.md) \
[Advertencia LNK4286 de las herramientas del vinculador](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)