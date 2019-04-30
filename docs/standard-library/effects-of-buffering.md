---
title: Efectos del almacenamiento en búfer
ms.date: 11/04/2016
helpviewer_keywords:
- buffers, effects of buffering
- buffering, effects of
ms.assetid: 5d544812-e95e-4f28-b15a-edef3f3414fd
ms.openlocfilehash: e10b28edffdfe3411f86c031bfd12ea886410e20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413793"
---
# <a name="effects-of-buffering"></a>Efectos del almacenamiento en búfer

En el ejemplo siguiente se muestran los efectos del almacenamiento en búfer. Se podría esperar que el programa imprima `please wait`, esperar 5 segundos y continuar. Pero no funcionará necesariamente de esta manera, porque la salida está almacenada en búfer.

```cpp
// effects_buffering.cpp
// compile with: /EHsc
#include <iostream>
#include <time.h>
using namespace std;

int main( )
{
   time_t tm = time( NULL ) + 5;
   cout << "Please wait...";
   while ( time( NULL ) < tm )
      ;
   cout << "\nAll done" << endl;
}
```

Para que el programa funcione lógicamente, el objeto `cout` debe vaciarse de forma automática cuando se muestre el mensaje. Para vaciar un objeto `ostream` , hay que enviarle el manipulador `flush` :

```cpp
cout <<"Please wait..." <<flush;
```

En este paso se vacía el búfer, lo que garantiza que el mensaje se imprima antes de la espera. También puede usar el `endl` manipulador, que vacía el búfer y da como resultado un retorno de carro/salto de línea, o puede usar el `cin` objeto. Este objeto (junto con los objetos `cerr` o `clog` ) suele estar vinculado al objeto `cout` . Por tanto, cualquier uso de `cin` (o de los objetos `cerr` o `clog` ) vacía el objeto `cout` .

## <a name="see-also"></a>Vea también

[Flujos de salida](../standard-library/output-streams.md)<br/>
