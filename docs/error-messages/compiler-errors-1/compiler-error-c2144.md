---
title: Error del compilador C2144 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2144
dev_langs: C++
helpviewer_keywords: C2144
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f85d1f8526a3f91087470b30c01e406d86fdd556
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2144"></a>Error del compilador C2144
error de sintaxis: 'type' debe ir precedido de 'token'  
  
 El compilador esperado `token` y encuentra `type` en su lugar.  
  
 Este error puede deberse a una falta llave de cierre, un paréntesis de cierre o un punto y coma.  
  
 También puede producirse el error C2144 al intentar crear una macro de una palabra clave CLR que contiene un carácter de espacio en blanco.  
  
 También puede ver error C2144 si está intentando reenvío de tipos. Vea [Type Forwarding (C++ / CLI)](../../windows/type-forwarding-cpp-cli.md) para obtener más información.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error C2144.  
  
```  
// C2144.cpp  
// compile with: /clr /c  
#define REF ref  
REF struct MyStruct0;   // C2144  
  
// OK  
#define REF1 ref struct  
REF1 MyStruct1;  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error C2144.  
  
```  
// C2144_2.cpp  
// compile with: /clr /c  
ref struct X {  
  
   property double MultiDimProp[,,] {   // C2144  
   // try the following line instead  
   // property double MultiDimProp[int , int, int] {  
      double get(int, int, int) { return 1; }  
      void set(int i, int j, int k, double l) {}  
   }  
  
   property double MultiDimProp2[] {   // C2144  
   // try the following line instead  
   // property double MultiDimProp2[int] {  
      double get(int) { return 1; }  
      void set(int i, double l) {}  
   }  
};  
```