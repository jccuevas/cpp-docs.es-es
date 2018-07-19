---
title: Error del compilador C3505 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3505
dev_langs:
- C++
helpviewer_keywords:
- C3505
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e0ea8edd3237db2085365450f43b4b955d36f33
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257662"
---
# <a name="compiler-error-c3505"></a>Error del compilador C3505

> no se puede cargar la biblioteca de tipos '*guid*'  
  
Error C3505 puede producirse si se está ejecutando lo 32 bits, hospedados x86 compilador cruzado de 64 bits, x64 destinos de 64 bits del equipo, porque el compilador se ejecuta bajo WOW64 y solo pueden leer desde el subárbol del registro de 32 bits.  
  
Puede resolver este error mediante la creación de versiones de 32 bits y 64 bits de la biblioteca de tipos que está intentando importar y, a continuación, registrar ambos.  O bien puede usar el compilador de 64 bits nativo, que exige que cambie su **directorios de VC ++** propiedad en el IDE para que apunte al compilador de 64 bits.  
  
Para obtener más información, vea  
  
-   [Procedimiento para habilitar un conjunto de herramientas de Visual C++ de 64 bits en la línea de comandos](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)  
  
-   [Cómo configurar proyectos de Visual C++ en plataformas de destino de 64 bits, x64](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)