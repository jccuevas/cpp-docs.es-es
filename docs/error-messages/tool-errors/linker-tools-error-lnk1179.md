---
title: Error de las herramientas del vinculador LNK1179
ms.date: 11/04/2016
f1_keywords:
- LNK1179
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
ms.openlocfilehash: a267019f1be08cc8dcffdff3b4ba0b73357cccd4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183962"
---
# <a name="linker-tools-error-lnk1179"></a>Error de las herramientas del vinculador LNK1179

archivo no válido o dañado: COMDAT ' nombredearchivo ' duplicado

Un módulo de objeto contiene dos o más COMDAT con el mismo nombre.

Este error puede deberse al uso de [/h](../../build/reference/h-restrict-length-of-external-names.md), que limita la longitud de los nombres externos y a [/GY](../../build/reference/gy-enable-function-level-linking.md), que empaqueta las funciones en COMDAT.

## <a name="example"></a>Ejemplo

En el código siguiente, `function1` y `function2` son idénticos en los primeros ocho caracteres. La compilación con **/GY** y **/H8** produce un error de vínculo.

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
