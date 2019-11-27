---
title: Advertencia del compilador (nivel 3) C4635
ms.date: 11/04/2016
f1_keywords:
- C4635
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
ms.openlocfilehash: b6fd45dc6c28c0d12eb2b2991f8a087b1841d1a9
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189146"
---
# <a name="compiler-warning-level-3-c4635"></a>Advertencia del compilador (nivel 3) C4635

destino del comentario del documento XML: XML incorrectamente formado: motivo

El compilador encontró algún problema con las etiquetas XML.  Corrija el problema y vuelva a compilar

El ejemplo siguiente genera la advertencia C4635:

```cpp
// C4635.cpp
// compile with: /doc /clr /W3 /c
/// <summary>
/// The contents of the folder have changed.
/// <summary/>   // C4635

// try the following line instead
// /// </summary>
public ref class Test {};
```

Observe que la salida de este ejemplo indica: **La etiqueta final 'member' no coincide con la etiqueta inicial 'summary'** .

El problema con este ejemplo es que la etiqueta de cierre de \<Resumen > tiene un formato incorrecto, y el compilador no la reconoce como la etiqueta de cierre de la \<>.  El compilador inserta en el archivo. xdc el \<etiqueta > miembro en cada compilación/doc.  Por lo tanto, el problema es que la etiqueta de cierre \</Member >, no coincide con la etiqueta de inicio anterior que el compilador ha procesado (\<> de resumen.