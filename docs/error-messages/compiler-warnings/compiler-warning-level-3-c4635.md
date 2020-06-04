---
title: Advertencia del compilador (nivel 3) C4635
ms.date: 11/04/2016
f1_keywords:
- C4635
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
ms.openlocfilehash: fd3bf6c1b14c6dae8e2fa95a54e2d4fbc4f295c5
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991855"
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
