---
title: Error de las herramientas del vinculador LNK1179
ms.date: 11/04/2016
f1_keywords:
- LNK1179
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
ms.openlocfilehash: 71aba1f20cfaf5b6b9ec33d43ebde594e381921f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391418"
---
# <a name="linker-tools-error-lnk1179"></a>Error de las herramientas del vinculador LNK1179

archivo no válido o dañado: 'filename' de COMDAT duplicado

Un módulo de objeto contiene dos o más COMDAT con el mismo nombre.

Este error puede deberse al uso [/H](../../build/reference/h-restrict-length-of-external-names.md), lo que limita la longitud de los nombres externos, y [/Gy](../../build/reference/gy-enable-function-level-linking.md), que empaqueta las funciones en COMDAT.

## <a name="example"></a>Ejemplo

En el código siguiente, `function1` y `function2` son idénticas en los primeros ocho caracteres. Compilar con **/Gy** y **/H8 se** produce un error de vínculo.

```
void function1(void);
void function2(void);

int main() {
    function1();
    function2();
}

void function1(void) {}
void function2(void) {}
```