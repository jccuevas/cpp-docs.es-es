---
title: Las herramientas del vinculador LNK4049 advertencia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4049
dev_langs:
- C++
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ad4e4adb492789639c71a25a2db774a80cd77c9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021764"
---
# <a name="linker-tools-warning-lnk4049"></a>Advertencia de las herramientas del vinculador LNK4049

el símbolo 'symbol' importado definido localmente

El símbolo se ha exportado desde tanto importado al programa.

Esta advertencia se genera el vinculador cuando se declara un símbolo utilizando el `__declspec(dllexport)` atributo en el archivo de un objeto de clase de almacenamiento y haga referencia a él mediante el uso de la `__declspec(dllimport)` atributo en otra.

Advertencia LNK4049 es una versión más general de [advertencia de las herramientas del vinculador LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md). El vinculador genera la advertencia LNK4049 cuando no se puede determinar de qué función se hizo referencia al símbolo importado.

Los casos más comunes donde LNK4049 se genera en lugar de LNK4217 son:

- Realizar la vinculación incremental mediante el uso de la [incremental](../../build/reference/incremental-link-incrementally.md) opción.

- Realizando la optimización de todo el programa mediante el uso de la [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) opción.

Para resolver LNK4049, pruebe uno de los siguientes:

- Quitar el `__declspec(dllimport)` nombre de la declaración de la declaración adelantada de símbolo que desencadenó la LNK4049. Puede buscar símbolos dentro de una imagen binaria mediante el **DUMPBIN** utilidad. El **DUMPBIN/símbolos** modificador muestra la tabla de símbolos COFF de la imagen. Para obtener más información sobre la **DUMPBIN** utilidad, vea [referencia de DUMPBIN](../../build/reference/dumpbin-reference.md).

- Deshabilitar temporalmente la optimización de todo el programa y vinculación incremental. Volver a compilar la aplicación generará la advertencia LNK4217, que incluirá el nombre de la función del que se hace referencia al símbolo importado. Quitar el `__declspec(dllimport)` declaración desde el símbolo importado y habilitar vinculación incremental o la optimización de todo el programa según sea necesario.

Aunque el código generado final se comportará correctamente, el código generado para llamar a la función importada es menos eficaz que llamar directamente a la función. Esta advertencia no aparecerá cuando se compila con la opción [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

Para obtener más información en Importar y exportar las declaraciones de datos, vea [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

## <a name="example"></a>Ejemplo

Vincular los dos módulos siguientes, se generará LNK4049. El primer módulo genera un archivo de objeto que contiene una única función exportada.

```
// LNK4049a.cpp
// compile with: /c

__declspec(dllexport) int func()
{
   return 3;
}
```

## <a name="example"></a>Ejemplo

El segundo módulo genera un archivo de objeto que contiene una declaración adelantada a la función exportada en el primer módulo, junto con una llamada a esta función dentro de la `main` función. Vincular este módulo con el primer módulo generará LNK4049. Quitar el `__declspec(dllimport)` declaración resolverá la advertencia.

```
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

[Advertencia de las herramientas del vinculador LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)