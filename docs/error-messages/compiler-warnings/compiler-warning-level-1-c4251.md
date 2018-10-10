---
title: Compilador advertencia (nivel 1) C4251 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4251
dev_langs:
- C++
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d964c375adf80caef3bb5a6eb06c67ef8e3e7200
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890054"
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