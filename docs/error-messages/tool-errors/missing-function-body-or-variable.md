---
title: "Falta el cuerpo de función o Variable | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs: C++
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 356d0f0a71feccee953a0b1bd7dc54bc64a0e233
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="missing-function-body-or-variable"></a>Cuerpo de función o variable no encontrados
Con un prototipo de función, el compilador puede continuar sin errores, pero el vinculador no puede resolver una llamada a una dirección porque no hay ningún código de función o variable espacio reservado. No verá este error hasta que cree una llamada a la función que debe resolver el vinculador.  
  
## <a name="example"></a>Ejemplo  
 La llamada de función en main producirá el error LNK2019 porque el prototipo permite al compilador que existe la función de reflexión.  El vinculador busca que no es así.  
  
```  
// LNK2019_MFBV.cpp  
// LNK2019 expected  
void DoSomething(void);  
int main() {  
   DoSomething();  
}  
```  
  
## <a name="example"></a>Ejemplo  
 En C++, asegúrese de que incluye la implementación de una función específica para una clase y no solamente el prototipo en la definición de clase. Si va a definir la clase fuera del archivo de encabezado, no olvide incluir el nombre de clase antes de la función (`Classname::memberfunction`).  
  
```  
// LNK2019_MFBV_2.cpp  
// LNK2019 expected  
struct A {  
   static void Test();  
};  
  
// Should be void A::Test() {}  
void Test() {}  
  
int main() {  
   A AObject;  
   AObject.Test();  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Error de las herramientas del vinculador LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)