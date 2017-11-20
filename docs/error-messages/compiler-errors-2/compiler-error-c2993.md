---
title: Error del compilador C2993 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2993
dev_langs: C++
helpviewer_keywords: C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a6306b2c3c632d25ee6b37a025516f759cc126a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2993"></a>Error del compilador C2993
'identificador': tipo no válido para el parámetro de plantilla sin tipo 'parameter'  
  
 No se puede declarar una plantilla con una estructura o unión argumento. Utilice punteros para pasar estructuras y uniones como parámetros de plantilla.  
  
 El ejemplo siguiente genera C2993:  
  
```  
// C2993.cpp  
// compile with: /c  
// C2993 expected  
struct MyStruct {  
   int a;char b;  
};  
  
template <class T, struct MyStruct S>   // C2993  
  
// try the following line instead  
// template <class T, struct MyStruct * S>  
class CMyClass {};  
```  
  
 Este error también se generará como resultado del trabajo de conformidad del compilador efectuado en Visual Studio .NET 2003: ya no se permite de parámetros de plantilla sin tipo de punto flotante. El estándar de C++ no permite parámetros de plantilla sin tipo de punto flotante.  
  
 Si se trata de una plantilla de función, utilice un argumento de función para transferir en flotante punto parámetro de plantilla sin tipo (este código será válido en las versiones de Visual Studio .NET 2003 y Visual Studio .NET de Visual C++). Si es una plantilla de clase, no hay ninguna solución alternativa fácil.  
  
```  
// C2993b.cpp  
// compile with: /c  
template<class T, float f> void func(T) {}   // C2993  
  
// OK  
template<class T>   void func2(T, float) {}  
```