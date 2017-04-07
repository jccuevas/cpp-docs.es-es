---
title: Compilador advertencia (nivel 2) C4275 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4275
dev_langs:
- C++
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: f9ecbe931c14cfde1d48438bdb76f70452e324d3
ms.lasthandoff: 04/01/2017

---
# <a name="compiler-warning-level-2-c4275"></a>Advertencia del compilador (nivel 2) C4275
no - utilizado interfaz DLL classkey 'identificador' como base para ha 'identificador' de interfaz DLL  
  
 Una clase exportada se derivó de una clase que no se ha exportado.  
  
 Para minimizar la posibilidad de daños en los datos al exportar una clase con [__declspec (dllexport)](../../cpp/dllexport-dllimport.md), asegúrese de que:  
  
-   Se tiene acceso a todos los datos estáticos a través de funciones que se exportan desde el archivo DLL.  
  
-   No hay ningún método entre línea de la clase puede modificar datos estáticos.  
  
-   No hay ningún método entre línea de la clase utiliza funciones de CRT ni otras funciones de biblioteca utilizan datos estáticos.  
  
-   Ninguna función de clase entre líneas utiliza funciones de CRT ni otras funciones de biblioteca donde, por ejemplo, obtiene acceso a datos estáticos.  
  
-   No hay métodos de la clase (con independencia de inclusión) pueden usar tipos en la creación de instancias en los archivos EXE y DLL tenga diferencias en los datos estáticos.  
  
 Puede evitar la exportación de clases definiendo un archivo DLL que define una clase con funciones virtuales y funciones que se puede llamar para crear instancias y eliminar objetos del tipo.  , A continuación, simplemente puede llamar a funciones virtuales en el tipo.  
  
 Para obtener más información acerca de cómo exportar plantillas, consulte [http://support.microsoft.com/default.aspx?scid=KB; EN-US; 168958](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958).  
  
 C4275 puede omitirse en Visual C++ si se deriva de un tipo en la biblioteca estándar de C++, compilar una versión de depuración (**/MTd**) y donde el mensaje de error del compilador hace referencia a _Container_base.  
  
```  
// C4275.cpp  
// compile with: /EHsc /MTd /W2 /c  
#include <vector>  
using namespace std;  
class Node;  
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275  
```
