---
title: Managed, unmanaged | Microsoft Docs
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
ms.openlocfilehash: 908ed745e82b17dd688f062ac7021c6adf3f4851
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "42541467"
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
  
Las funciones se compilan como administradas de forma predeterminada cuando se utiliza `/clr`.  
  
Al aplicar estas pragmas:  
  
- Agregue la pragma que precede a una función, pero no dentro del cuerpo de la función.  
  
- Agregue la pragma después de las instrucciones `#include`. No use estas pragmas antes de las instrucciones `#include`.  
  
El compilador omite la **administrada** y **no administrado** pragmas si `/clr` no se utiliza en la compilación.  
  
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