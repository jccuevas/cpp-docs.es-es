---
title: "Advertencia del compilador (nivel 1) C4407 | Microsoft Docs"
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
  - "C4407"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4407"
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4407
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

al convertir entre distintas representaciones de puntero a miembro, el compilador puede generar código incorrecto  
  
 Se detectó una conversión incorrecta.  
  
 La advertencia C4407 puede generarse debido al trabajo de conformidad del compilador realizado para Visual C\+\+ 2005.  El Puntero\-a\- miembro ahora requiere un nombre completo y el dirección\- de operator \(&\).  
  
 La advertencia C4407 puede aparecer si se convierten tipos de un puntero a miembro de herencia múltiple a un puntero a miembro de herencia simple.  A veces esto puede funcionar, pero a veces no puede porque la representación de puntero a miembro de herencia simple no contiene información suficiente.  Puede ser útil compilar con **\/vmm** \(para obtener más información, vea [\/vmm, \/vms, \/vmv \(Representación de propósito general\)](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)\).  También se puede tratar de reorganizar las clases base. El compilador detecta una falta de información en la conversión porque una clase base está a un desplazamiento distinto de cero de la derivada.  
  
 El código siguiente genera el error C4407:  
  
```  
// C4407.cpp  
// compile with: /W1 /c  
struct C1 {};  
struct C2 {};  
struct C3 : C1, C2 {};  
  
typedef void(C3::*PMF_C3)();  
typedef void(C2::*PMF_C2)();  
  
PMF_C2 f1(PMF_C3 pmf) {  
   return (PMF_C2)pmf;   // C4407, change type of cast,  
   // or reverse base class inheritance of C3 (i.e. : C2, C1)  
}  
```