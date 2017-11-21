---
title: Compilador advertencia (nivel 1) C4348 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4348
dev_langs: C++
helpviewer_keywords: C4348
ms.assetid: 816010eb-6079-48d5-a41b-0fc4d67cfe4c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ec91b979c6c7e55e7a0d11b486ed62731dbbeecd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4348"></a>Advertencia del compilador (nivel 1) C4348
'type': nueva definición de parámetro predeterminado: parámetro número  
  
 Se ha redefinido un parámetro de plantilla.  
  
 El ejemplo siguiente genera C4348:  
  
```  
// C4348.cpp  
// compile with: /LD /W1  
template <class T=int> struct A;   // forward declaration  
  
template <class T=int> struct A { };   
// C4348, redefinition of default parameter  
// try the following line instead  
// template <class T> struct A { };  
```