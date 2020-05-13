---
title: Advertencia del compilador (nivel 2) C4275
ms.date: 02/08/2019
f1_keywords:
- C4275
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
ms.openlocfilehash: ad12c1c27006a57c8339e9dad82e4d8e1a239a6e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162002"
---
# <a name="compiler-warning-level-2-c4275"></a>Advertencia del compilador (nivel 2) C4275

> clase '*class_1*' de interfaz no dll usada como base para la clase '*class_2*' de la interfaz dll

Una clase exportada se derivó de una clase que no se exportó.

Para minimizar la posibilidad de que se dañen los datos al exportar una clase con [__declspec (dllexport)](../../cpp/dllexport-dllimport.md), asegúrese de que:

- Se tiene acceso a todos los datos estáticos a través de las funciones que se exportan desde el archivo DLL.

- Ningún método insertado de la clase puede modificar los datos estáticos.

- Ningún método insertado de la clase utiliza funciones de CRT u otras funciones de biblioteca que utilicen datos estáticos.

- Ninguna función de clase insertada usa funciones de CRT ni otras funciones de biblioteca, donde se tiene acceso a los datos estáticos.

- Ninguno de los métodos de la clase (independientemente de la inserción) puede utilizar tipos en los que la creación de instancias de los archivos EXE y DLL tenga diferencias de datos estáticos.

Puede evitar la exportación de clases definiendo un archivo DLL que define una clase con funciones virtuales y funciones a las que se puede llamar para crear instancias y eliminar objetos del tipo.  Después, puede llamar a funciones virtuales en el tipo.

C4275 se puede omitir en C++ visual si se deriva de un tipo en la C++ biblioteca estándar, compilando una versión de depuración ( **/MTD**) y donde el mensaje de error del compilador hace referencia a `_Container_base`.

```cpp
// C4275.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275
```
