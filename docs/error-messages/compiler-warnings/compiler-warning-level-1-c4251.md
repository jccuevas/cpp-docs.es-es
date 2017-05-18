---
title: Compilador C4251 de advertencia (nivel 1) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4251
dev_langs:
- C++
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
caps.latest.revision: 16
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: b75c3e6c93c0963a692b210b158339ea5e9eacac
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4251"></a>Advertencia del compilador (nivel 1) C4251
'identificador': clase 'tipo' necesita tener una interfaz dll que usarán los clientes de ' tipo2 '  
  
 Para minimizar la posibilidad de daños en los datos al exportar una clase con [__declspec (dllexport)](../../cpp/dllexport-dllimport.md), asegúrese de que:  
  
-   Todos los datos estáticos es el acceso a través de funciones que se exportan desde el archivo DLL.  
  
-   Ningún método entre líneas de su clase puede modificar datos estáticos.  
  
-   Ningún método entre líneas de su clase utiliza funciones de CRT ni otras funciones de biblioteca utilizan datos estáticos (vea [posibles errores pasando CRT Objects Across DLL Boundaries](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md) para obtener más información).  
  
-   No hay métodos de la clase (con independencia de inclusión entre líneas) puede utilizar tipos donde la creación de instancias en los archivos EXE y DLL tienen diferencias de datos estáticos.  
  
 Puede evitar la exportación de clases definiendo un archivo DLL que define una clase con funciones virtuales y funciones que se puede llamar para crear instancias y eliminar objetos del tipo.  Puede, a continuación, simplemente debe llamar a funciones virtuales en el tipo.  
  
 Para obtener más información acerca de la exportación de plantillas, consulte [http://support.microsoft.com/default.aspx?scid=KB; EN-US;&16895;8](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958).  
  
 C4251 se puede omitir si deriva de un tipo en la biblioteca estándar de C++, compilar una versión de depuración (**/MTd**) y donde el mensaje de error del compilador hace referencia a _Container_base.  
  
```  
// C4251.cpp  
// compile with: /EHsc /MTd /W2 /c  
#include <vector>  
using namespace std;  
class Node;  
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251  
```
