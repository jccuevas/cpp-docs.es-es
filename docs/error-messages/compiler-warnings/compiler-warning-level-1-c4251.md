---
title: Advertencia del compilador (nivel 1) C4251
ms.date: 04/21/2020
f1_keywords:
- C4251
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
ms.openlocfilehash: 9f261d3deb7f1cac8cd5c60b920e0be49bc8b7a6
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032335"
---
# <a name="compiler-warning-level-1-c4251"></a>Advertencia del compilador (nivel 1) C4251

> '*type*' : class '*type1*' necesita tener dll-interface para ser utilizado por los clientes de la clase '*type2*'

## <a name="remarks"></a>Observaciones

Para minimizar la posibilidad de daños en los datos al exportar una clase declarada como [__declspec(dllexport),](../../cpp/dllexport-dllimport.md)asegúrese de que:

- Se tiene acceso a todos los datos estáticos a través de las funciones que se exportan desde el archivo DLL.

- Ningún método insertado de la clase puede modificar los datos estáticos.

- Ningún método insertado de la clase utiliza funciones CRT u otras funciones de biblioteca que utilizan datos estáticos. Para obtener más información, vea [Errores potenciales al pasar objetos CRT a través](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)de los límites de DLL.

- Ningún método de la clase (ya sea insertado o no) puede usar tipos donde la creación de instancias en EXE y DLL tienen diferencias de datos estáticos.

Puede evitar problemas al exportar una clase desde un archivo DLL: defina la clase para que tenga funciones virtuales y funciones para crear instancias y eliminar objetos del tipo. A continuación, puede llamar a funciones virtuales en el tipo.

C4251 se puede omitir si la clase se deriva de un tipo en la biblioteca estándar de C++, está compilando `_Container_base`una versión de depuración (**/MTd**) y donde el mensaje de error del compilador hace referencia a .

## <a name="example"></a>Ejemplo

Este ejemplo exporta una `VecWrapper` clase `std::vector`especializada derivada de .

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllexport) VecWrapper : vector<Node *> {};   // C4251
```
