---
title: "naked (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "naked_cpp"
  - "naked"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec (palabra clave) [C++], naked"
  - "naked __declspec (palabra clave)"
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# naked (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Para las funciones declaradas con el atributo `naked`, el compilador genera código sin código de prólogo y epílogo.  Puede utilizar esta característica para escribir sus propias secuencias de código de prólogo\/epílogo mediante código del ensamblador alineado.  Las funciones naked son especialmente útiles al escribir controladores de dispositivos virtuales.  Tenga en cuenta que el atributo `naked` solo es válido en x86 y ARM, y no está disponible en [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)].  
  
## Sintaxis  
  
```  
__declspec(naked) declarator  
```  
  
## Comentarios  
 Puesto que el atributo `naked` solo es pertinente para la definición de una función y no es un modificador de tipo, las funciones naked deben utilizar la sintaxis de atributo extendido y la palabra clave [\_\_declspec](../cpp/declspec.md).  
  
 El compilador no puede generar una función insertada para una función marcada con el atributo naked, incluso aunque la función esté marcada también con la palabra clave [\_\_forceinline](../misc/inline-inline-forceinline.md).  
  
 El compilador emite un error si el atributo `naked` se aplica a algo distinto de la definición de un método que no es miembro.  
  
## Ejemplos  
 En este código se define una función con el atributo `naked`:  
  
```  
__declspec( naked ) int func( formal_parameters ) {}  
```  
  
 O bien, como alternativa:  
  
```  
#define Naked __declspec( naked )  
Naked int func( formal_parameters ) {}  
```  
  
 El atributo `naked` solo afecta a la naturaleza de la generación de código del compilador para las secuencias de prólogo y epílogo de la función.  No afecta al código que se genera para llamar a esas funciones.  Por tanto, el atributo `naked` no se considera parte del tipo de la función y los punteros a función no pueden tener el atributo `naked`.  Además, el atributo `naked` no se puede aplicar a una definición de datos.  Por ejemplo, en este ejemplo de código se genera un error:  
  
```  
__declspec( naked ) int i;       // Error--naked attribute not  
                                 // permitted on data declarations.  
```  
  
 El atributo `naked` solo es pertinente para la definición de la función y no se puede especificar en el prototipo de la función.  Por ejemplo, esta declaración genera un error del compilador:  
  
```  
__declspec( naked ) int func();  // Error--naked attribute not   
                                 // permitted on function declarations  
```  
  
 **Específicos de Microsoft: END**  
  
## Vea también  
 [\_\_declspec](../cpp/declspec.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [Llamadas de función naked](../cpp/naked-function-calls.md)