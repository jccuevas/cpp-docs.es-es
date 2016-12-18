---
title: "region, endregion | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.endregion"
  - "endregion_CPP"
  - "region_CPP"
  - "vc-pragma.region"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "endregion (pragma)"
  - "pragma (directivas), endregion"
  - "pragma (directivas), región"
  - "region (pragma)"
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# region, endregion
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**\#pragma region** permite especificar un bloque de código que se puede expandir o contraer cuando se utiliza la [característica de esquematización](../Topic/Outlining.md) del editor de código de Visual Studio.  
  
## Sintaxis  
  
```  
#pragma region name  
#pragma endregion comment  
```  
  
#### Parámetros  
 `comment` \(opcional\)  
 Un comentario que aparecerá en el editor de código.  
  
 *name* \(opcional\)  
 El nombre de la región.  Este nombre aparecerá en el editor de código.  
  
## Comentarios  
 **\#pragma endregion** marca el final de un bloque **\#pragma region**.  
  
 Un bloque `#region` se debe terminar con **\#pragma endregion**.  
  
## Ejemplo  
  
```  
// pragma_directives_region.cpp  
#pragma region Region_1  
void Test() {}  
void Test2() {}  
void Test3() {}  
#pragma endregion Region_1  
  
int main() {}  
```  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)