---
title: CL invoca el vinculador
ms.date: 11/04/2016
helpviewer_keywords:
- compiling source code [C++], without linking
- invoking linker from the compiler
- LINK tool [C++], invoking from CL compiler
- cl.exe compiler [C++], compiling without linking
- cl.exe compiler [C++], controlling linker
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
ms.openlocfilehash: 1f9bb466ae89b8e3491b027a98b28935e7c8b523
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440186"
---
# <a name="cl-invokes-the-linker"></a>CL invoca el vinculador

CL invoca automáticamente al enlazador después de compilar a menos que se use la opción/c. CL pasa al enlazador los nombres de los archivos. obj creados durante la compilación y los nombres de otros archivos especificados en la línea de comandos. El enlazador usa las opciones enumeradas en la variable de entorno LINK. Puede usar la opción/Link para especificar las opciones del enlazador en la línea de comandos de CL. Las opciones que siguen a la opción/Link reemplazan a las de la variable de entorno LINK. Las opciones de la tabla siguiente suprimen la vinculación.

|Opción|Descripción|
|------------|-----------------|
|/c|Compilar sin vincular|
|/E,/EP,/P|Preprocesar sin compilar o vincular|
|/Zg|Generar prototipos de función|
|/Zs|Comprobar la sintaxis|

Para obtener más información sobre la vinculación, vea [Opciones del enlazador MSVC](linker-options.md).

## <a name="example"></a>Ejemplo

Suponga que está compilando tres archivos de código fuente de C: MAIN. c, MOD1. c y MOD2. c. Cada archivo incluye una llamada a una función definida en un archivo diferente:

- MAIN. c llama a la función `func1` en MOD1. c y la función `func2` en MOD2. c.

- MOD1. c llama a las funciones de la biblioteca estándar `printf_s` y `scanf_s`.

- MOD2. c llama a las funciones de gráficos denominadas `myline` y `mycircle`, que se definen en una biblioteca denominada gráfico. lib.

Para compilar este programa, compile con la siguiente línea de comandos:

```
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib
```

En primer lugar, CL compila los archivos de código fuente de C y crea los archivos objeto MAIN. obj, MOD1. obj y MOD2. obj. El compilador coloca el nombre de la biblioteca estándar en cada archivo. obj. Para obtener más información, vea [usar la biblioteca en tiempo de ejecución](md-mt-ld-use-run-time-library.md).

CL pasa al enlazador los nombres de los archivos. obj, junto con el nombre de gráfico. lib. El enlazador resuelve las referencias externas de la siguiente manera:

1. En MAIN. obj, la referencia a `func1` se resuelve utilizando la definición de MOD1. obj; la referencia a `func2` se resuelve utilizando la definición de MOD2. obj.

1. En MOD1. obj, las referencias a `printf_s` y `scanf_s` se resuelven con las definiciones de la biblioteca que el vinculador encuentra con nombre dentro de MOD1. obj.

1. En MOD2. obj, las referencias a `myline` y `mycircle` se resuelven con las definiciones de gráfico. lib.

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Establecer las opciones del compilador](compiler-command-line-syntax.md)
