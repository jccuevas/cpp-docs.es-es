---
title: "Advertencia del compilador (nivel 1) C4383 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4383"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4383"
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4383
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operador\_desreferenciar\_instancias' : el significado de desreferenciar un identificador puede cambiar cuando existe un operador 'operador' definido por el usuario; escriba el operador como función estática para que sea explícito con relación al operando  
  
 Cuando se agrega un reemplazo de instancias definido por el usuario del operador de desreferenciación en un tipo administrado, es probable que se reemplace la capacidad del operador de eliminación de referencias del tipo para devolver el objeto del identificador.  Considere la posibilidad de escribir un operador de desreferenciación estático definido por el usuario.  
  
 Para obtener más información, vea [Identificador a un operador de objeto \(^\)](../../windows/handle-to-object-operator-hat-cpp-component-extensions.md) y [Operador de referencia de seguimiento](../../windows/tracking-reference-operator-cpp-component-extensions.md).  
  
 Además, un operador de instancias no está disponible para otros compiladores de lenguaje a través de los metadatos a los que hace referencia.  Para obtener más información, vea [Operadores definidos por el usuario](../../dotnet/user-defined-operators-cpp-cli.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4383.  
  
```  
// C4383.cpp  
// compile with: /clr /W1  
  
ref struct S {  
   int operator*() { return 0; }   // C4383  
};  
  
ref struct T {  
   static int operator*(T%) { return 0; }  
};   
  
int main() {  
   S s;  
   S^ pS = %s;  
  
   T t;  
   T^ pT = %t;  
   T% rT = *pT;  
}  
```