---
title: "Efectos del almacenamiento en búfer | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- buffers, effects of buffering
- buffering, effects of
ms.assetid: 5d544812-e95e-4f28-b15a-edef3f3414fd
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: e834b5be6b7d31d1f1516799462d57330bf4ceb2
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="effects-of-buffering"></a>Efectos del almacenamiento en búfer
En el ejemplo siguiente se muestran los efectos del almacenamiento en búfer. Se podría esperar que el programa imprima `please wait`, esperar 5 segundos y continuar. Pero no funcionará necesariamente de esta manera, porque la salida está almacenada en búfer.  
  
```  
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
  
```  
cout <<"Please wait..." <<flush;  
```  
  
 En este paso se vacía el búfer, lo que garantiza que el mensaje se imprima antes de la espera. También puede usar el `endl` manipulador, que vacía el búfer y se genera un retorno de carro/salto de línea, o puede usar el `cin` objeto. Este objeto (junto con los objetos `cerr` o `clog` ) suele estar vinculado al objeto `cout` . Por tanto, cualquier uso de `cin` (o de los objetos `cerr` o `clog` ) vacía el objeto `cout` .  
  
## <a name="see-also"></a>Vea también  
 [Flujos de salida](../standard-library/output-streams.md)


