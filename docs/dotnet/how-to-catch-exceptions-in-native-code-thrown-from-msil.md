---
title: 'Cómo: detectar excepciones en código nativo iniciado desde MSIL | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3d5c1efde1f98ac3f9fdccb19039373d5cfe6be6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>Cómo: Detectar excepciones en código nativo iniciadas desde MSIL
En código nativo, puede detectar las excepciones de C++ nativo de MSIL.  Puede capturar excepciones de CLR con `__try` y `__except`.  
  
 Para obtener más información, consulte [control de excepciones estructurado (C/C ++)](../cpp/structured-exception-handling-c-cpp.md) y [control de excepciones de C++](../cpp/cpp-exception-handling.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente define un módulo con dos funciones, uno que produce una excepción nativo y otro que produce una excepción de MSIL.  
  
```  
// catch_MSIL_in_native.cpp  
// compile with: /clr /c  
void Test() {  
   throw ("error");  
}  
  
void Test2() {  
   throw (gcnew System::Exception("error2"));  
}  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente define un módulo que detecta un nativo y la excepción de MSIL.  
  
```  
// catch_MSIL_in_native_2.cpp  
// compile with: /clr catch_MSIL_in_native.obj  
#include <iostream>  
using namespace std;  
void Test();  
void Test2();  
  
void Func() {  
   // catch any exception from MSIL  
   // should not catch Visual C++ exceptions like this  
   // runtime may not destroy the object thrown  
   __try {  
      Test2();  
   }  
   __except(1) {  
      cout << "caught an exception" << endl;  
   }  
  
}  
  
int main() {  
   // catch native C++ exception from MSIL  
   try {  
      Test();  
   }  
   catch(char * S) {  
      cout << S << endl;  
   }  
   Func();  
}  
```  
  
```Output  
error  
caught an exception  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones](../windows/exception-handling-cpp-component-extensions.md)