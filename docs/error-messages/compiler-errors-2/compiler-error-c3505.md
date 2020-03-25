---
title: Error del compilador C3505
ms.date: 11/04/2016
f1_keywords:
- C3505
helpviewer_keywords:
- C3505
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
ms.openlocfilehash: 0c67eb46208c35c1b11a74898107ad3c0e6e570d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200856"
---
# <a name="compiler-error-c3505"></a>Error del compilador C3505

> no se puede cargar la biblioteca de tipos '*GUID*'

C3505 puede deberse a que se está ejecutando el compilador cruzado de 32 bits hospedado en x86 para destinos de 64 bits x64 en un equipo de 64 bits, porque el compilador se ejecuta bajo WOW64 y solo puede leer desde el subárbol del registro de 32 bits.

Puede resolver este error mediante la compilación de las versiones de 32 bits y de 64 bits de la biblioteca de tipos que está intentando importar y, a continuación, registrarlas.  O bien, puede usar el compilador nativo de 64 bits, que requiere cambiar la propiedad de los **directorios de VC + +** en el IDE para que apunte al compilador de 64 bits.

Para obtener más información, vea

- [Procedimiento para habilitar un conjunto de herramientas de Visual C++ de 64 bits en la línea de comandos](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)

- [Cómo configurar proyectos de Visual C++ en plataformas de destino de 64 bits, x64](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)
