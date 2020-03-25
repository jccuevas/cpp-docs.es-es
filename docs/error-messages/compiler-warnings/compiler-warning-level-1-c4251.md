---
title: Advertencia del compilador (nivel 1) C4251
ms.date: 11/04/2016
f1_keywords:
- C4251
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
ms.openlocfilehash: 8a723b7ce7fc79fb6be9c9dd2b500631098622b0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163224"
---
# <a name="compiler-warning-level-1-c4251"></a>Advertencia del compilador (nivel 1) C4251

' Identifier ': la clase ' type ' debe tener la interfaz dll que usarán los clientes de la clase ' tipo2 '

Para minimizar la posibilidad de que se dañen los datos al exportar una clase con [__declspec (dllexport)](../../cpp/dllexport-dllimport.md), asegúrese de que:

- Todos los datos estáticos son accesibles a través de las funciones que se exportan desde el archivo DLL.

- Ningún método insertado de la clase puede modificar los datos estáticos.

- Ningún método insertado de la clase usa funciones de CRT u otras funciones de biblioteca usan datos estáticos (vea [posibles errores al pasar objetos de CRT a través](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md) de los límites de dll para obtener más información).

- Ninguno de los métodos de la clase (independientemente de la inserción) puede utilizar tipos en los que la creación de instancias de los archivos EXE y DLL tenga diferencias de datos estáticos.

Puede evitar la exportación de clases definiendo un archivo DLL que define una clase con funciones virtuales y funciones a las que se puede llamar para crear instancias y eliminar objetos del tipo.  Después, puede llamar a funciones virtuales en el tipo.

C4251 se puede omitir si se deriva de un tipo en la C++ biblioteca estándar, compilando una versión de depuración ( **/MTD**) y donde el mensaje de error del compilador hace referencia a _Container_base.

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251
```
