---
title: Las herramientas del vinculador LNK1179 Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1179
dev_langs:
- C++
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d22ebb329d390d44aea44ff9dc6f3bf2f86a1d26
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117463"
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