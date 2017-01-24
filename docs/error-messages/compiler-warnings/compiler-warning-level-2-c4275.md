---
title: "Advertencia del compilador (nivel 2) C4275 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4275"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4275"
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 2) C4275
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se ha utilizado una interfaz no de DLL clave de clase 'identificador' como base para la interfaz DLL clave de clase 'identificador'  
  
 Se derivó una clase exportada de una clase que no se había exportado.  
  
 Para minimizar la posibilidad de dañar los datos al exportar una clase con [\_\_declspec \(dllexport\)](../../cpp/dllexport-dllimport.md), asegúrese de que:  
  
-   Se tiene acceso a todos los datos estáticos a través de funciones que se exportan del archivo DLL.  
  
-   Ningún método entre líneas de su clase puede modificar los datos estáticos.  
  
-   Ningún método entre líneas de la clase utiliza funciones de CRT ni otras funciones de biblioteca que utilizan datos estáticos.  
  
-   Ninguna función de clase entre líneas utiliza funciones de CRT ni otras funciones de biblioteca donde, por ejemplo, se tiene acceso a datos estáticos.  
  
-   Ningún método de su clase \(sea o no entre líneas\) puede utilizar tipos donde la creación de instancias en el EXE y archivo DLL tengan diferencias en los datos estáticos.  
  
 Es posible evitar la exportación de clases definiendo una DLL que defina una clase con funciones virtuales, y funciones a las que se puede llamar para crear instancias y eliminar objetos del tipo.  Después se puede llamar a funciones virtuales en el tipo.  
  
 Para obtener más información sobre cómo exportar plantillas, vea [http:\/\/support.microsoft.com\/default.aspx?scid\=KB;EN\-US;168958](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958).  
  
 El error C4275 se puede omitir en Visual C\+\+ si está derivando de un tipo de la Biblioteca estándar de C\+\+, si está compilando una versión de depuración \(**\/MTd**\) y si el mensaje de error del compilador hace referencia a \_Container\_base.  
  
```  
// C4275.cpp  
// compile with: /EHsc /MTd /W2 /c  
#include <vector>  
using namespace std;  
class Node;  
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275  
```