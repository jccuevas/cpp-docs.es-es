---
title: Advertencia del compilador (nivel 1) C4251
ms.date: 11/04/2016
f1_keywords:
- C4251
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
ms.openlocfilehash: d2fff1d2f30c4ac80af6d5b9ca452fa5f30f5a15
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649662"
---
# <a name="compiler-warning-level-1-c4251"></a>Advertencia del compilador (nivel 1) C4251

'identifier': clase 'type' debe tener una interfaz dll que va a usar los clientes de la clase 'tipo2'

Para minimizar la posibilidad de daños en los datos al exportar una clase con [__declspec (dllexport)](../../cpp/dllexport-dllimport.md), asegúrese de que:

- Todos los datos estáticos es el acceso a través de funciones que se exportan desde el archivo DLL.

- Ningún método entre líneas de la clase puede modificar datos estáticos.

- Ningún método entre líneas de la clase utiliza funciones de CRT ni otras funciones de biblioteca utilizan datos estáticos (vea [posibles errores pasando CRT objetos a través de los límites de DLL](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md) para obtener más información).

- No hay métodos de la clase (con independencia de inclusión entre líneas) puede utilizar tipos que la creación de instancias en los archivos EXE y DLL tienen diferencias de datos estáticos.

Puede evitar la exportación de clases definiendo un archivo DLL que define una clase con funciones virtuales y funciones que se puede llamar para crear instancias y eliminar objetos del tipo.  , A continuación, simplemente puede llamar a funciones virtuales en el tipo.

C4251 puede omitirse si se va a derivar de un tipo en la biblioteca estándar de C++, compilar una versión de depuración (**/MTd**) y donde el mensaje de error del compilador hace referencia a _Container_base.

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251
```