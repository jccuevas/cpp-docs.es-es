---
title: CL invoca el vinculador
ms.date: 11/04/2016
f1_keywords:
- cl
helpviewer_keywords:
- compiling source code [C++], without linking
- invoking linker from the compiler
- LINK tool [C++], invoking from CL compiler
- cl.exe compiler [C++], compiling without linking
- cl.exe compiler [C++], controlling linker
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
ms.openlocfilehash: f8d8c5e1b0ca4d2a35a57683fea2e6de12747860
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821494"
---
# <a name="cl-invokes-the-linker"></a>CL invoca el vinculador

CL invoca automáticamente el vinculador después de compilar, a menos que se utiliza la opción /c. CL pasa al vinculador los nombres de los archivos .obj creados durante la compilación y los nombres de cualquier otro archivo especificado en la línea de comandos. El vinculador utiliza las opciones enumeradas en la variable de entorno LINK. Puede usar la opción /link para especificar las opciones del vinculador en la línea de comandos de CL. Las opciones que siguen la opción /link invalidación la de la variable de entorno LINK. Las opciones en la tabla siguiente suprimen la vinculación.

|Opción|Descripción|
|------------|-----------------|
|/c|Compilar sin vinculación|
|/E, /EP, /P|Preprocesar sin compilar ni vincular|
|/Zg|Generar prototipos de función|
|/Zs|Comprobar la sintaxis|

Para obtener más información acerca de la vinculación, vea [las opciones del vinculador MSVC](linker-options.md).

## <a name="example"></a>Ejemplo

Supongamos que está compilando archivos de código fuente de C tres: MAIN.c, MOD1.c y MOD2.c. Cada archivo incluye una llamada a una función definida en un archivo diferente:

- MAIN.c llama a la función `func1` en MOD1.c y la función `func2` de MOD2.c.

- MOD1.c llama a las funciones de biblioteca estándar `printf_s` y `scanf_s`.

- MOD2.c llama a las funciones de gráficos `myline` y `mycircle`, que se definen en la biblioteca MYGRAPH.lib.

Para generar este programa, compile con la siguiente línea de comandos:

```
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib
```

En primer lugar, CL compila los archivos de código fuente de C y crea los archivos objeto MAIN.obj, MOD1.obj y MOD2.obj. El compilador coloca el nombre de la biblioteca estándar en cada archivo obj. Para obtener más información, consulte [utilizar la biblioteca en tiempo de ejecución](md-mt-ld-use-run-time-library.md).

CL pasa los nombres de los archivos .obj, junto con el nombre de MYGRAPH.lib al vinculador. El vinculador resuelve las referencias externas como sigue:

1. En MAIN.obj, la referencia a `func1` se resuelve mediante la definición de MOD1.obj; la referencia a `func2` se resuelve con la definición de MOD2.obj.

1. En MOD1.obj, las referencias a `printf_s` y `scanf_s` se resuelven usando las definiciones de la biblioteca que el vinculador encuentre mencionada en MOD1.obj.

1. En MOD2.obj, las referencias a `myline` y `mycircle` se resuelven con las definiciones de MYGRAPH.lib.

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)<br/>
[Establecer las opciones del compilador](compiler-command-line-syntax.md)
