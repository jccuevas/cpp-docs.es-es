---
title: "Falta el cuerpo de función o Variable | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 4bac7b2942f9d72674b8092dc7bf64174dd3c349
ms.openlocfilehash: c80a5626e7f674ddca7d44e94aa8ab64c735c81e
ms.lasthandoff: 04/24/2017

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
