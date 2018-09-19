---
title: Del compilador (nivel 2) de la advertencia C4275 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4275
dev_langs:
- C++
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7cb8f397243bb6531f33ac5e444914cfa36e5fe1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022641"
---
# <a name="compiler-warning-level-2-c4275"></a>Advertencia del compilador (nivel 2) C4275

no - utilizado una interfaz DLL classkey 'identificador' como base para classkey 'identificador' de una interfaz DLL

Una clase exportada se derivó de una clase que no se ha exportado.

Para minimizar la posibilidad de daños en los datos al exportar una clase con [__declspec (dllexport)](../../cpp/dllexport-dllimport.md), asegúrese de que:

- Se tiene acceso a todos los datos estáticos a través de funciones que se exportan desde el archivo DLL.

- Ningún método entre líneas de la clase puede modificar datos estáticos.

- Ningún método entre líneas de la clase utiliza funciones de CRT ni otras funciones de biblioteca utilizan datos estáticos.

- Ninguna función de la clase inline usa funciones de CRT ni otras funciones de biblioteca donde, por ejemplo, tener acceso a datos estáticos.

- No hay métodos de la clase (con independencia de inclusión entre líneas) puede utilizar tipos que la creación de instancias en los archivos EXE y DLL tienen diferencias de datos estáticos.

Puede evitar la exportación de clases definiendo un archivo DLL que define una clase con funciones virtuales y funciones que se puede llamar para crear instancias y eliminar objetos del tipo.  , A continuación, simplemente puede llamar a funciones virtuales en el tipo.

Para obtener más información sobre la exportación de plantillas, consulte [ http://support.microsoft.com/default.aspx?scid=KB; EN-US; 168958](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958).

C4275 puede omitirse en Visual C++ si va a derivar de un tipo en la biblioteca estándar de C++, compilar una versión de depuración (**/MTd**) y donde el mensaje de error del compilador hace referencia a _Container_base.

```
// C4275.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275
```