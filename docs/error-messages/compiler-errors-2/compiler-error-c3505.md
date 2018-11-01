---
title: Error del compilador C3505
ms.date: 11/04/2016
f1_keywords:
- C3505
helpviewer_keywords:
- C3505
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
ms.openlocfilehash: 5730102371d00ebaf3ae05fdefb70184b58d7c18
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481784"
---
# <a name="compiler-error-c3505"></a>Error del compilador C3505

> no se puede cargar la biblioteca de tipos '*guid*'

C3505 puede producirse si se ejecutan lo 32 bits, hospedados x86 compilador cruzado de 64 bits, x64 destinos de 64 bits del equipo, porque el compilador se ejecuta bajo WOW64 y solo pueden leer desde el subárbol del registro de 32 bits.

Puede resolver este error mediante la creación de versiones de 32 bits y 64 bits de la biblioteca de tipos que está intentando importar y, a continuación, registrar ambos.  O bien puede usar el compilador nativo de 64 bits, que requiere que se cambie su **directorios de VC ++** propiedad en el IDE para que apunte al compilador de 64 bits.

Para obtener más información, vea

- [Procedimiento para habilitar un conjunto de herramientas de Visual C++ de 64 bits en la línea de comandos](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)

- [Cómo configurar proyectos de Visual C++ en plataformas de destino de 64 bits, x64](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)