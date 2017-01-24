---
title: "Error irrecuperable C1308 | Microsoft Docs"
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
  - "C1308"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1308"
ms.assetid: 46177997-069e-433a-8e20-93c846d78ffd
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1308
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se admite la vinculación de ensamblados  
  
 Un .netmodule se permite como entrada del vinculador, pero un ensamblado no.  Este error se puede generar cuando se intenta vincular un ensamblado compilado con `/clr:safe`.  
  
 Para obtener más información, vea [Archivos .netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md).  
  
 El código siguiente genera el error C1308:  
  
```  
// C1308.cpp  
// compile with: /clr:safe /LD  
public ref class MyClass {  
public:  
   int i;  
};  
```  
  
 y, a continuación,  
  
```  
// C1308b.cpp  
// compile with: /clr /link C1308b.obj C1308.dll  
// C1308 expected  
#using "C1308.dll"  
int main() {  
   MyClass ^ my = gcnew MyClass();  
}  
```