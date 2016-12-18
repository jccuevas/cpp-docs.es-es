---
title: "Error del compilador C3675 | Microsoft Docs"
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
  - "C3675"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3675"
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3675
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : se ha reservado porque 'propiedad' está definido  
  
 Cuando declara una propiedad simple, el compilador genera los métodos de descriptor de acceso get y set, y dichos nombres están presentes en el ámbito de su programa.  Los nombres generados por el compilador se forman anteponiendo get\_ y set\_ al nombre de la propiedad.  Por consiguiente, no puede declarar funciones con el mismo nombre que los descriptores de acceso generados por compilador.  
  
 Para obtener más información, vea [propiedad](../../windows/property-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3675.  
  
```  
// C3675.cpp  
// compile with: /clr /c  
ref struct C {  
public:  
   property int Size;  
   int get_Size() { return 0; }   // C3675  
};  
```