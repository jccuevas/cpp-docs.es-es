---
title: Advertencia del compilador (nivel 1) C4910
ms.date: 11/04/2016
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: 49cbbf3369fc4765d93e67e2dca84a4d975560d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242895"
---
# <a name="compiler-warning-level-1-c4910"></a>Advertencia del compilador (nivel 1) C4910

'\<identificador >': '__declspec (dllexport)' y 'extern' son incompatibles en una instancia explícita

La creación de instancias de plantilla explícita denominada  *\<identificador >* es modificado por el `__declspec(dllexport)` y `extern` palabras clave. Sin embargo, estas palabras clave son mutuamente excluyentes. La palabra clave `__declspec(dllexport)` implica que se cree una instancia de la clase de plantilla, mientras que la palabra clave `extern` que no se creen automáticamente instancias de la clase de plantilla.

## <a name="see-also"></a>Vea también

[Creación de instancias explícita](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[Reglas generales y limitaciones](../../cpp/general-rules-and-limitations.md)