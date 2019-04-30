---
title: Advertencia del compilador (nivel 2) C4275
ms.date: 02/08/2019
f1_keywords:
- C4275
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
ms.openlocfilehash: 6e0e80d465d77bd4fe99fbcaa98e289b8a4c8b63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349690"
---
# <a name="compiler-warning-level-2-c4275"></a>Advertencia del compilador (nivel 2) C4275

> no - la clase interfaz DLL*clase_1*'se usa como base para la clase de interfaz DLL'*class_2*'

Una clase exportada se derivó de una clase que no se ha exportado.

Para minimizar la posibilidad de daños en los datos al exportar una clase con [__declspec (dllexport)](../../cpp/dllexport-dllimport.md), asegúrese de que:

- Se tiene acceso a todos los datos estáticos a través de funciones que se exportan desde el archivo DLL.

- Ningún método entre líneas de la clase puede modificar datos estáticos.

- Ningún método entre línea de la clase utiliza funciones de CRT u otras funciones de biblioteca que utilizan datos estáticos.

- Ninguna función de la clase inline usa funciones de CRT, u otras funciones de biblioteca, donde tener acceso a datos estáticos.

- No hay métodos de la clase (con independencia de inclusión entre líneas) puede utilizar tipos que la creación de instancias en los archivos EXE y DLL tienen diferencias de datos estáticos.

Puede evitar la exportación de clases definiendo un archivo DLL que define una clase con funciones virtuales y funciones que se puede llamar para crear instancias y eliminar objetos del tipo.  , A continuación, simplemente puede llamar a funciones virtuales en el tipo.

C4275 puede omitirse en Visual C++ si va a derivar de un tipo en la biblioteca estándar de C++, compilar una versión de depuración (**/MTd**) y donde el mensaje de error del compilador hace referencia a `_Container_base`.

```cpp
// C4275.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275
```