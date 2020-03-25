---
title: Advertencia del compilador (nivel 1) C4910
ms.date: 11/04/2016
f1_keywords:
- C4910
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: dc5feb3613e45134a08e493b397eb738fffee8a9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174783"
---
# <a name="compiler-warning-level-1-c4910"></a>Advertencia del compilador (nivel 1) C4910

'\<identificador > ': ' __declspec (dllexport) ' y ' extern ' son incompatibles en una creación de instancias explícita

Las palabras clave `__declspec(dllexport)` y `extern` modifican la creación de instancias explícita de la plantilla denominada *\<identificador >* . Sin embargo, estas palabras clave son mutuamente excluyentes. La palabra clave `__declspec(dllexport)` implica que se cree una instancia de la clase de plantilla, mientras que la palabra clave `extern` que no se creen automáticamente instancias de la clase de plantilla.

## <a name="see-also"></a>Consulte también

[Creación de instancias explícita](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[Reglas generales y limitaciones](../../cpp/general-rules-and-limitations.md)
