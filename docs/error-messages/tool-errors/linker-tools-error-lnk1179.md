---
title: Error de las herramientas del vinculador LNK1179
ms.date: 11/04/2016
f1_keywords:
- LNK1179
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
ms.openlocfilehash: d85693cec11ef53a6bbbb60d8ced716d2a0bb131
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754336"
---
# <a name="linker-tools-error-lnk1179"></a>Error de las herramientas del vinculador LNK1179

archivo no válido o corrupto: duplicado COMDAT 'nombre de archivo'

Un módulo de objeto contiene dos o más COMDAT con el mismo nombre.

Este error puede deberse al uso de [/H](../../build/reference/h-restrict-length-of-external-names.md), que limita la longitud de los nombres externos, y [/Gy](../../build/reference/gy-enable-function-level-linking.md), que empaqueta las funciones en COMDAT.

## <a name="example"></a>Ejemplo

En el código `function1` `function2` siguiente, y son idénticos en los primeros ocho caracteres. La compilación con **/Gy** y **/H8** produce un error de vínculo.

```cpp
void function1(void);
void function2(void);

int main() {
    function1();
    function2();
}

void function1(void) {}
void function2(void) {}
```
