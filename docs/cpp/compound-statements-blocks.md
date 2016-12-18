---
title: "Instrucciones compuestas (Bloques) | Microsoft Docs"
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
  - "}"
  - "{"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bloques, acerca de los bloques"
  - "instrucciones compuestas"
ms.assetid: 23855939-7430-498e-8936-0c70055ea701
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Instrucciones compuestas (Bloques)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una instrucción compuesta consta de cero o más instrucciones entre llaves \(**{ }**\).  Una instrucción compuesta se puede utilizar en cualquier lugar donde se espere una instrucción.  Las instrucciones compuestas normalmente se denominan "bloques".  
  
## Sintaxis  
  
```  
  
{ [ statement-list ] }  
```  
  
## Comentarios  
 En el ejemplo siguiente se utiliza una instrucción compuesta como la parte *statement* de la instrucción **if** \(vea [Instrucción if](../cpp/if-else-statement-cpp.md) para obtener más detalles sobre la sintaxis\):  
  
```  
if( Amount > 100 )  
{  
    cout << "Amount was too large to handle\n";  
    Alert();  
}  
else  
    Balance -= Amount;  
```  
  
> [!NOTE]
>  Dado que una declaración es una instrucción, una declaración puede ser una de las instrucciones de *statement\-list*.  Por consiguiente, los nombres declarados dentro de una instrucción compuesta, pero no declarados explícitamente como static, tienen ámbito local y \(para objetos\) duración.  Vea [Ámbito](../cpp/scope-visual-cpp.md) para obtener más información sobre el tratamiento de los nombres con ámbito local.  
  
## Vea también  
 [Información general sobre las instrucciones de C\+\+](../cpp/overview-of-cpp-statements.md)