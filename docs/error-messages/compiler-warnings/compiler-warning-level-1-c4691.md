---
title: "Advertencia del compilador (nivel 1) C4691 | Microsoft Docs"
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
  - "C4691"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4691"
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4691
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo': se esperaba el tipo al que se hace referencia en el ensamblado 'archivo' sin referencia; se utilizó el tipo definido en la unidad de traducción actual  
  
 No se hace referencia al archivo de metadatos que contiene la definición de tipos original y el compilador utiliza una definición de tipos local.  
  
 En caso de que se esté recompilando *file*, C4691 se puede omitir o desactivar con el pragma [warning](../../preprocessor/warning.md).  Es decir, si el archivo que se está generando es el mismo en el que el compilador espera encontrar la definición de tipos, se puede omitir la advertencia C4691.  
  
 No obstante, puede producirse un comportamiento inesperado si el compilador utiliza una definición que no procede del mismo ensamblado al que se hace referencia en metadatos. Los tipos de CLR se establecen como tales no sólo por el nombre del tipo, sino también por el ensamblado.  Es decir, un tipo Z del ensamblado z.dll es diferente de un tipo Z del ensamblado y.dll.  
  
## Ejemplo  
 Este ejemplo contiene la definición de tipos original.  
  
```  
// C4691_a.cpp  
// compile with: /clr /LD /W1  
public ref class Original_Type {};  
```  
  
## Ejemplo  
 Este ejemplo hace referencia a C4691\_a.dll y declara un campo de tipo Original\_Type.  
  
```  
// C4691_b.cpp  
// compile with: /clr /LD  
#using "C4691_a.dll"  
public ref class Client {  
public:  
   Original_Type^ ot;  
};  
```  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4691.  Observe que este ejemplo contiene una definición para Original\_Type y no hace referencia a C4691a.dll.  
  
 Para resolverlo, haga referencia al archivo de metadatos que contiene la definición de tipos original y quite la declaración y la definición locales.  
  
```  
// C4691_c.cpp  
// compile with: /clr /LD /W1  
// C4691 expected  
  
// Uncomment the following line to resolve.  
// #using "C4691_a.dll"  
#using "C4691_b.dll"  
  
// Delete the following line to resolve.  
ref class Original_Type;  
  
public ref class MyClass : Client {};  
```