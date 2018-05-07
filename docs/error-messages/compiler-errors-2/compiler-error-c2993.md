---
title: Error del compilador C2993 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2993
dev_langs:
- C++
helpviewer_keywords:
- C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e25e70a9d16ee166772cf03ea1837afaf14cae29
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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