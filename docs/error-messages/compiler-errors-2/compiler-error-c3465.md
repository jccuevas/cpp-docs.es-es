---
title: Error del compilador C3465 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3465
dev_langs:
- C++
helpviewer_keywords:
- C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1965b616ec3eb8c7de50f3a76b10e41f3579954c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3465"></a>Error del compilador C3465
para usar el tipo 'type' debe hacer referencia al ensamblado 'assembly'  
  
 El reenvío de tipos funcionará para una aplicación cliente hasta que recompile el cliente. Cuando recompile, necesitará una referencia para cada ensamblado que contenga la definición de un tipo utilizado en la aplicación cliente.  
  
 Para obtener más información, consulte [Type Forwarding (C++ / CLI)](../../windows/type-forwarding-cpp-cli.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera un ensamblado que contiene la nueva ubicación de un tipo.  
  
```  
// C3465.cpp  
// compile with: /clr /LD  
public ref class R {  
public:  
   ref class N {};  
};  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera un ensamblado que se usa para contener la definición del tipo, pero ahora contiene sintaxis de reenvío para el tipo.  
  
```  
// C3465_b.cpp  
// compile with: /clr /LD  
#using "C3465.dll"  
[ assembly:TypeForwardedTo(R::typeid) ];  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C3465.  
  
```  
// C3465_c.cpp  
// compile with: /clr  
// C3465 expected  
#using "C3465_b.dll"  
// Uncomment the following line to resolve.  
// #using "C3465.dll"  
  
int main() {  
   R^ r = gcnew R();  
}  
```