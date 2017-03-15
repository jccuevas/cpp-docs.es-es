---
title: Advertencia de compilador (nivel 2) de la advertencia C4275 | Documentos de Microsoft
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
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 873a96d4595b75ff6b9567500723c32d7ba5bd2b
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-2-c4275"></a>Advertencia del compilador (nivel 2) C4275
no usa classkey 'identificador de interfaz DLL' como base para la interfaz DLL classkey 'identificador'  
  
 Una clase exportada se derivó de una clase que no se ha exportado.  
  
 Para minimizar la posibilidad de daños en los datos al exportar una clase con [__declspec (dllexport)](../../cpp/dllexport-dllimport.md), asegúrese de que:  
  
-   Todos los datos estáticos se tiene acceso a través de funciones que se exportan desde el archivo DLL.  
  
-   Ningún método entre líneas de su clase puede modificar datos estáticos.  
  
-   Ningún método entre líneas de su clase utiliza funciones de CRT ni otras funciones de biblioteca utilizan datos estáticos.  
  
-   Ninguna función de clase entre líneas utiliza funciones de CRT ni otras funciones de biblioteca donde, por ejemplo, acceder a datos estáticos.  
  
-   No hay métodos de la clase (con independencia de inclusión entre líneas) puede utilizar tipos donde la creación de instancias en los archivos EXE y DLL tienen diferencias de datos estáticos.  
  
 Puede evitar la exportación de clases definiendo un archivo DLL que define una clase con funciones virtuales y funciones que se puede llamar para crear instancias y eliminar objetos del tipo.  Puede, a continuación, simplemente debe llamar a funciones virtuales en el tipo.  
  
 Para obtener más información acerca de la exportación de plantillas, consulte [http://support.microsoft.com/default.aspx?scid=KB; EN-US;&16895;8](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958).  
  
 Advertencia C4275 puede omitirse en Visual C++ si deriva de un tipo en la biblioteca estándar de C++, compilar una versión de depuración (**/MTd**) y donde el mensaje de error del compilador hace referencia a _Container_base.  
  
```  
// C4275.cpp  
// compile with: /EHsc /MTd /W2 /c  
#include <vector>  
using namespace std;  
class Node;  
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275  
```
