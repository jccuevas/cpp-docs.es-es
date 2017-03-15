---
title: "Error de las herramientas del vinculador LNK1312 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1312"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1312"
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error de las herramientas del vinculador LNK1312
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

archivo dañado o no válido: no se puede importar el ensamblado  
  
 Al crear un ensamblado, se ha pasado a la opción del vinculador **\/ASSEMBLYMODULE** un archivo que no es un módulo o ensamblado compilado con **\/clr**.  Si ha pasado un archivo objeto a **\/ASSEMBLYMODULE**, simplemente hay que pasar el objeto directamente al vinculador, en lugar de pasárselo a **\/ASSEMBLYMODULE**.  
  
## Ejemplo  
 El ejemplo siguiente creó el archivo .obj.  
  
```  
// LNK1312.cpp  
// compile with: /clr /LD  
public ref class A {  
public:  
   int i;  
};  
```  
  
## Ejemplo  
 El ejemplo siguiente genera el error LNK1312.  
  
```  
// LNK1312_b.cpp  
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj  
// LNK1312 error expected  
public ref class M {};  
```