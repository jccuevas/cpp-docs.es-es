---
title: Inicialización de CRT
ms.date: 11/04/2016
helpviewer_keywords:
- CRT initialization [C++]
ms.assetid: e7979813-1856-4848-9639-f29c86b74ad7
ms.openlocfilehash: 03126b8fdf1c3824b114d822c269655c22e5ee9f
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446684"
---
# <a name="crt-initialization"></a>Inicialización de CRT

En este tema se describe cómo el CRT inicializa estados globales en código nativo.

De forma predeterminada, el vinculador incluye la biblioteca de CRT, que proporciona su propio código de inicio. Este código de inicio inicializa la biblioteca de CRT, llama a los inicializadores globales y, después, llama a la función `main` proporcionada por el usuario para las aplicaciones de consola.

## <a name="initializing-a-global-object"></a>Inicialización de un objeto global

Observe el código siguiente:

```
int func(void)
{
    return 3;
}

int gi = func();

int main()
{
    return gi;
}
```

Según el estándar de C o C++, se debe llamar a `func()` antes de ejecutar `main()`. Pero, ¿quién llama?

Una forma de determinar esta cuestión consiste en establecer un punto de interrupción en `func()`, depurar la aplicación y examinar la pila. Esto es posible porque el código fuente de CRT se incluye en Visual Studio.

Al examinar las funciones en la pila, observará que CRT está en bucle a través de una lista de punteros a función y una llamada a cada una de ellos a medida que los encuentra. Estas funciones son similares a `func()` o constructores de instancias de clase.

La biblioteca de CRT obtiene la lista de punteros de función del compilador de Microsoft C++. Cuando el compilador encuentra un inicializador global, genera un inicializador dinámico en la sección `.CRT$XCU` (donde `CRT` es el nombre de sección y `XCU` es el nombre de grupo). Para obtener una lista de estos inicializadores dinámicos, ejecute el comando **dumpbin /all main.obj** y, después, busque la sección `.CRT$XCU` (cuando main.cpp se compila como un archivo de C++, y no como un archivo de C). La operación debe ser similar a la siguiente:

```
SECTION HEADER #6
.CRT$XCU name
       0 physical address
       0 virtual address
       4 size of raw data
     1F2 file pointer to raw data (000001F2 to 000001F5)
     1F6 file pointer to relocation table
       0 file pointer to line numbers
       1 number of relocations
       0 number of line numbers
40300040 flags
         Initialized Data
         4 byte align
         Read Only

RAW DATA #6
  00000000: 00 00 00 00                                      ....

RELOCATIONS #6
                                                Symbol    Symbol
Offset    Type              Applied To         Index     Name
--------  ----------------  -----------------  --------  ------
00000000  DIR32                      00000000         C  ??__Egi@@YAXXZ (void __cdecl `dynamic initializer for 'gi''(void))
```

CRT define dos punteros:

- `__xc_a` en `.CRT$XCA`

- `__xc_z` en `.CRT$XCZ`

Los dos grupos no tienen ningún otro símbolo definido, excepto `__xc_a` y `__xc_z`.

Ahora, cuando el vinculador lee varios grupos `.CRT`, los combina en una sección y los ordena alfabéticamente. Esto significa que los inicializadores globales definidos por el usuario (que el compilador de Microsoft C++ coloca en `.CRT$XCU`) siempre irán después de `.CRT$XCA` y antes de `.CRT$XCZ`.

La sección será similar a la siguiente:

```
.CRT$XCA
            __xc_a
.CRT$XCU
            Pointer to Global Initializer 1
            Pointer to Global Initializer 2
.CRT$XCZ
            __xc_z
```

Por lo tanto, la biblioteca de CRT utiliza `__xc_a` y `__xc_z` para determinar el inicio y el final de la lista de inicializadores globales, debido a la forma en que están colocados en memoria después de cargar la imagen.

## <a name="see-also"></a>Vea también

[Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)
