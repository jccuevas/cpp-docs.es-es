---
title: Advertencia de las herramientas del vinculador LNK4253
ms.date: 11/04/2016
f1_keywords:
- LNK4253
helpviewer_keywords:
- LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
ms.openlocfilehash: d2fd7238a3f57b11b91813bd40b66cb3e9f47202
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352532"
---
# <a name="linker-tools-warning-lnk4253"></a>Advertencia de las herramientas del vinculador LNK4253

sección 'sección1' no combinada en 'section2'; ya se combinó en 'sección3'

El vinculador detectó varias solicitudes de combinación en conflicto. El vinculador omitirá una de las solicitudes.

Un **/MERGE** se encuentra la opción o directiva y la `from` sección ya se ha combinado con una sección diferente debido a una anterior **/MERGE** opción o directiva (o debido a una combinación implícita el enlazador).

Para resolver LNK4253, quite una de las solicitudes de combinación.

Cuando el destino es x86 máquinas y los destinos de Windows CE (ARM, MIPS, SH4 y control de posición) con Visual C++, el. Sección de CRT es de solo lectura. Si el código depende del comportamiento anterior (. Las secciones de CRT son de sólo lectura), podría obtener comportamientos inesperados.

Para obtener más información, vea

- [/MERGE (Combinar secciones)](../../build/reference/merge-combine-sections.md)

- [comment (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, se indica al vinculador para combinar el `.rdata` sección dos veces, pero en secciones diferentes. El ejemplo siguiente genera la advertencia LNK4253.

```
// LNK4253.cpp
// compile with: /W1 /link /merge:.rdata=text2
// LNK4253 expected
#pragma comment(linker, "/merge:.rdata=.text")
int main() {}
```