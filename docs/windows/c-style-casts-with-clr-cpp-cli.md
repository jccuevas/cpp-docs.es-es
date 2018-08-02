---
title: Conversiones de estilo C con /CLR (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- C-style casts and /clr
ms.assetid: d2a4401a-156a-4da9-8d12-923743e26913
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0ffb2e5a7276925c5f03d06a909803d001532f35
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464589"
---
# <a name="c-style-casts-with-clr-ccli"></a>Conversiones de estilo C con /clr (C++/CLI)
El siguiente tema se aplica solo a Common Language Runtime.  
  
 Cuando se usa con tipos CLR, el compilador intenta asignar el estilo C convertirse en una de las conversiones que se enumeran a continuación, en el orden siguiente:  
  
1.  const_cast  
  
2.  safe_cast  
  
3.  safe_cast plus const_cast  
  
4.  static_cast  
  
5.  static_cast plus const_cast  
  
 Si ninguna de las conversiones de tipos enumerados anteriormente es válida y si el tipo de la expresión y el tipo de destino son tipos de referencia CLR, conversión de estilo C se asigna a una comprobación de tiempo de ejecución (instrucción de MSIL castclass). En caso contrario, una conversión de estilo C se considera no válida y el compilador emite un error.  
  
## <a name="remarks"></a>Comentarios  
 No se recomienda una conversión de estilo C. Cuando se compila con [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md), utilice [safe_cast](../windows/safe-cast-cpp-component-extensions.md).  
  
 El ejemplo siguiente muestra una conversión de estilo C que se asigna a un **const_cast**.  
  
```cpp  
// cstyle_casts_1.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {};  
int main() {  
   const R^ constrefR = gcnew R();  
   R^ nonconstR = (R^)(constrefR);   
}  
```  
  
 El ejemplo siguiente muestra una conversión de estilo C que se asigna a un **safe_cast**.  
  
```cpp  
// cstyle_casts_2.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   Object ^ o = "hello";  
   String ^ s = (String^)o;  
}  
```  
  
 El ejemplo siguiente muestra una conversión de estilo C que se asigna a un **safe_cast** plus **const_cast**.  
  
```cpp  
// cstyle_casts_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {};  
ref struct R2 : public R {};  
  
int main() {  
   const R^ constR2 = gcnew R2();  
   try {  
   R2^ b2DR = (R2^)(constR2);  
   }  
   catch(InvalidCastException^ e) {  
      System::Console::WriteLine("Invalid Exception");  
   }  
}  
```  
  
 El ejemplo siguiente muestra una conversión de estilo C que se asigna a un **static_cast**.  
  
```cpp  
// cstyle_casts_4.cpp  
// compile with: /clr  
using namespace System;  
  
struct N1 {};  
struct N2 {  
   operator N1() {  
      return N1();  
   }  
};  
  
int main() {  
   N2 n2;  
   N1 n1 ;  
   n1 = (N1)n2;  
}  
```  
  
 El ejemplo siguiente muestra una conversión de estilo C que se asigna a un **static_cast** plus **const_cast**.  
  
```cpp  
// cstyle_casts_5.cpp  
// compile with: /clr  
using namespace System;  
struct N1 {};  
  
struct N2 {  
   operator const N1*() {  
      static const N1 n1;  
      return &n1;  
   }  
};  
  
int main() {  
   N2 n2;  
   N1* n1 = (N1*)(const N1*)n2;   // const_cast + static_cast  
}  
```  
  
 El ejemplo siguiente muestra una conversión de estilo C que se asigna a una comprobación en tiempo de ejecución.  
  
```cpp  
// cstyle_casts_6.cpp  
// compile with: /clr  
using namespace System;  
  
ref class R1 {};  
ref class R2 {};  
  
int main() {  
   R1^ r  = gcnew R1();  
   try {  
      R2^ rr = ( R2^)(r);  
   }  
   catch(System::InvalidCastException^ e) {  
      Console::WriteLine("Caught expected exception");  
   }  
}  
```  
  
 El ejemplo siguiente muestra un válido conversión de estilo C, lo que hace que el compilador emita un error.  
  
```cpp  
// cstyle_casts_7.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   String^s = S"hello";  
   int i = (int)s;   // C2440  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Opción del compilador: **/clr**  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)