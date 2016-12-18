---
title: "Efectos del almacenamiento en b&#250;fer | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "búferes, efectos del almacenamiento en búfer"
  - "almacenamiento en búfer, efectos del"
ms.assetid: 5d544812-e95e-4f28-b15a-edef3f3414fd
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Efectos del almacenamiento en b&#250;fer
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el ejemplo siguiente se muestran los efectos del almacenamiento en búfer. Se podría esperar que el programa imprima `please wait`, esperar 5 segundos y continuar. Pero no funcionará necesariamente de esta manera, porque la salida está almacenada en búfer.  
  
```  
// effects_buffering.cpp // compile with: /EHsc #include <iostream> #include <time.h> using namespace std; int main( ) { time_t tm = time( NULL ) + 5; cout << "Please wait..."; while ( time( NULL ) < tm ) ; cout << "\nAll done" << endl; }  
```  
  
 Para que el programa funcione lógicamente, el objeto `cout` debe vaciarse de forma automática cuando se muestre el mensaje. Para vaciar un objeto `ostream`, hay que enviarle el manipulador `flush`:  
  
```  
cout << "Please wait..." << flush;  
```  
  
 En este paso se vacía el búfer, lo que garantiza que el mensaje se imprima antes de la espera. También se puede usar el manipulador `endl`, que vacía el búfer y genera un salto de línea de retorno de carro o se puede usar el objeto `cin`. Este objeto \(junto con los objetos `cerr` o `clog`\) suele estar vinculado al objeto `cout`. Por tanto, cualquier uso de `cin` \(o de los objetos `cerr` o `clog`\) vacía el objeto `cout`.  
  
## Vea también  
 [Flujos de salida](../standard-library/output-streams.md)