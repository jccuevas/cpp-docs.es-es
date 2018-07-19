---
title: Managed, unmanaged | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.unmanaged
- managed_CPP
- unmanaged_CPP
- vc-pragma.managed
dev_langs:
- C++
helpviewer_keywords:
- managed pragma
- pragmas, unmanaged
- pragmas, managed
- unmanaged pragma
ms.assetid: f072ddcc-e1ec-408a-8ce1-326ddb60e4a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 316866ac047b607ec4c92d7c6d4f8ff233ed9a3f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846381"
---
# <a name="managed-unmanaged"></a>managed, unmanaged
Habilite el control de nivel de función para compilar las funciones como administradas o no administradas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      #pragma managed  
#pragma unmanaged  
#pragma managed([push,] on | off)  
#pragma managed(pop)  
```  
  
## <a name="remarks"></a>Comentarios  
 El [/CLR](../build/reference/clr-common-language-runtime-compilation.md) opción del compilador proporciona control de nivel de módulo para compilar las funciones como administradas o no administrado.  
  
 Una función no administrada se compilará para la plataforma nativa, a la cual Common Language Runtime pasará la ejecución de esa parte del programa.  
  
 Las funciones se compilan como administradas de forma predeterminada cuando **/CLR** se utiliza.  
  
 Al aplicar estas pragmas:  
  
-   Agregue la pragma que precede a una función, pero no dentro del cuerpo de la función.  
  
-   Agregue la pragma después de las instrucciones `#include`. No use estas pragmas antes de las instrucciones `#include`.  
  
 El compilador omite la `managed` y `unmanaged` pragmas si **/CLR** no se utiliza en la compilación.  
  
 Cuando se crea una función de plantilla, el estado de pragma en el momento de definir la plantilla determina si es managed o unmanaged.  
  
 Para obtener más información, consulte [inicialización de ensamblados mixtos](../dotnet/initialization-of-mixed-assemblies.md).  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// pragma_directives_managed_unmanaged.cpp  
// compile with: /clr  
#include <stdio.h>  
  
// func1 is managed  
void func1() {  
   System::Console::WriteLine("In managed function.");  
}  
  
// #pragma unmanaged  
// push managed state on to stack and set unmanaged state  
#pragma managed(push, off)  
  
// func2 is unmanaged  
void func2() {  
   printf("In unmanaged function.\n");  
}  
  
// #pragma managed  
#pragma managed(pop)  
  
// main is managed  
int main() {  
   func1();  
   func2();  
}  
```  
  
```Output  
In managed function.  
In unmanaged function.  
```  
  
## <a name="see-also"></a>Vea también  
 [Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)