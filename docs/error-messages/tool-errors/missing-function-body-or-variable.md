---
title: "Cuerpo de funci&#243;n o variable no encontrados | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cuerpo de función"
  - "variables, falta"
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Cuerpo de funci&#243;n o variable no encontrados
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Si sólo hay un prototipo de función, el compilador puede continuar sin errores, pero el vinculador no puede resolver una llamada a una dirección porque no hay código de función o espacio de variables reservado.  No aparecerá este error hasta que cree una llamada a la función que debe resolver el vinculador.  
  
## Ejemplo  
 La llamada a la función en Main producirá el error LNK2019 porque el prototipo permitirá creer al compilador que existe la función.  El vinculador descubrirá que no es así.  
  
```  
// LNK2019_MFBV.cpp  
// LNK2019 expected  
void DoSomething(void);  
int main() {  
   DoSomething();  
}  
```  
  
## Ejemplo  
 En C\+\+, asegúrese de que incluye la implementación de una función especifica de una clase y no solamente el prototipo en la definición de la clase.  Si define la clase fuera del archivo de encabezado, no se olvide de incluir el nombre de la clase antes de la función \(`Classname``::``memberfunction`\).  
  
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
  
## Vea también  
 [Error de las herramientas del vinculador LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)