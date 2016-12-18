---
title: "Error del compilador C2844 | Microsoft Docs"
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
  - "C2844"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2844"
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2844
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'miembro' : no puede ser un miembro de la interfaz 'interfaz'  
  
 Una [clase de interfaz](../../windows/interface-class-cpp-component-extensions.md) no puede contener un miembro de datos a menos que sea también una propiedad.  
  
 Cualquier otra cosa que no sea una propiedad o función miembro no está permitida en una interfaz.  Es más, no se permiten constructores, destructores ni operadores.  
  
 El código siguiente genera el error C2844:  
  
```  
// C2844a.cpp  
// compile with: /clr /c  
public interface class IFace {  
   int i;   // C2844  
   // try the following line instead  
   // property int Size;  
};  
```  
  
 El código siguiente genera el error C2844:  
  
```  
// C2844b.cpp  
// compile with: /clr:oldSyntax /c  
#using <mscorlib.dll>  
__gc __interface IFace {  
   int i;   // C2844  
   // try the following line instead  
   // __property int Size { get; set; };  
};  
```