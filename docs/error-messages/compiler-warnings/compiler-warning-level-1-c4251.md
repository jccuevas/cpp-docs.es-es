---
title: Compilador advertencia (nivel 1) C4251 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4251
dev_langs: C++
helpviewer_keywords: C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5b220913d97755547a9cb35fe326f9fb9a06e40a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4251"></a>Advertencia del compilador (nivel 1) C4251
'identificador': clase 'type' debe tener una interfaz dll que se usará para los clientes de ' tipo2 '  
  
 Para minimizar la posibilidad de daños en los datos al exportar una clase con [__declspec (dllexport)](../../cpp/dllexport-dllimport.md), asegúrese de que:  
  
-   Todos los datos estáticos es el acceso a través de funciones que se exportan desde el archivo DLL.  
  
-   No hay ningún método entre línea de la clase puede modificar datos estáticos.  
  
-   No hay ningún método entre línea de la clase utiliza funciones de CRT ni otras funciones de biblioteca utilizan datos estáticos (vea [posibles errores pasar CRT objetos a través de los límites de DLL](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md) para obtener más información).  
  
-   No hay métodos de la clase (con independencia de inclusión) pueden usar tipos en la creación de instancias en los archivos EXE y DLL tenga diferencias en los datos estáticos.  
  
 Puede evitar la exportación de clases definiendo un archivo DLL que define una clase con funciones virtuales y funciones que se puede llamar para crear instancias y eliminar objetos del tipo.  , A continuación, simplemente puede llamar a funciones virtuales en el tipo.  
  
 Para obtener más información acerca de cómo exportar plantillas, consulte [http://support.microsoft.com/default.aspx?scid=KB; EN-US; 168958](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958).  
  
 C4251 se puede omitir si se deriva de un tipo en la biblioteca estándar de C++, compilar una versión de depuración (**/MTd**) y donde el mensaje de error del compilador hace referencia a _Container_base.  
  
```  
// C4251.cpp  
// compile with: /EHsc /MTd /W2 /c  
#include <vector>  
using namespace std;  
class Node;  
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251  
```