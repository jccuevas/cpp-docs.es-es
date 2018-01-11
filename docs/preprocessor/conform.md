---
title: se ajustan | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- conform_CPP
- vc-pragma.conform
dev_langs: C++
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5f876c1b921a00c251010d22e2cdd000a405a651
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="conform"></a>conform
**Específicos de C++**  
  
 Especifica el comportamiento de tiempo de ejecución de la [/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) opción del compilador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma conform(name [, show ] [, on | off ] [ [, push | pop ] [, identifier ] ] )  
```  
  
#### <a name="parameters"></a>Parámetros  
 *name*  
 Especifica el nombre de la opción del compilador que se va a modificar. El único valor válido *nombre* es `forScope`.  
  
 **Mostrar** (opcional)  
 Hace que la configuración actual de *nombre* (true o false) se muestre mediante un mensaje de advertencia durante la compilación. Por ejemplo: `#pragma conform(forScope, show)`.  
  
 **activado, desactivado**(opcional)  
 Establecer *nombre* a **en** permite la [/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) opción del compilador. El valor predeterminado es **desactivar**.  
  
 **inserción** (opcional)  
 Inserta el valor actual de *nombre* en la pila interna del compilador. Si especifica *identificador*, puede especificar el **en** o **desactivar** valor *nombre* en insertarse en la pila. Por ejemplo: `#pragma conform(forScope, push, myname, on)`.  
  
 **confirmación** (opcional)  
 Establece el valor de *nombre* en el valor en la parte superior de la pila interna del compilador y, a continuación, extrae la pila. Si se especifica el identificador con **pop**, se extrae la pila hasta que encuentra el registro con *identificador*, que también se extrae; el valor actual de *nombre* en el registro siguiente en la pila se convierte en el nuevo valor de *nombre*. Si especifica pop con un *identificador* que no está en un registro en la pila, el **pop** se omite.  
  
 *identificador*(opcional)  
 Se puede incluir en un **inserción** o **pop** comando. Si *identificador* se utiliza, a continuación, un **en** o **desactivar** también se puede utilizar el especificador.  
  
## <a name="example"></a>Ejemplo  
  
```  
// pragma_directive_conform.cpp  
// compile with: /W1  
// C4811 expected  
#pragma conform(forScope, show)  
#pragma conform(forScope, push, x, on)  
#pragma conform(forScope, push, x1, off)  
#pragma conform(forScope, push, x2, off)  
#pragma conform(forScope, push, x3, off)  
#pragma conform(forScope, show)  
#pragma conform(forScope, pop, x1)  
#pragma conform(forScope, show)  
  
int main() {}  
```  
  
## <a name="see-also"></a>Vea también  
 [Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)