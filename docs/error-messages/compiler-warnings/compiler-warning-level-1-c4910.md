---
title: Advertencia del compilador (nivel 1) C4910
ms.date: 11/04/2016
f1_keywords:
- C4910
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: a3f29cb895da8c06ed43dd5c9956426f3f6014f1
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810716"
---
# <a name="compiler-warning-level-1-c4910"></a>Advertencia del compilador (nivel 1) C4910

'\<identificador > ': ' __declspec (dllexport) ' y ' extern ' son incompatibles en una creación de instancias explícita

Las palabras clave `__declspec(dllexport)` y `extern` modifican la creación de instancias explícita de la plantilla denominada *\<identificador >* . Sin embargo, estas palabras clave son mutuamente excluyentes. La palabra clave `__declspec(dllexport)` implica que se cree una instancia de la clase de plantilla, mientras que la palabra clave `extern` que no se creen automáticamente instancias de la clase de plantilla.

## <a name="see-also"></a>Vea también

[Creación de instancias explícita](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[Reglas generales y limitaciones](../../cpp/general-rules-and-limitations.md)