---
title: "Error irrecuperable del compilador de recursos RC1020 | Microsoft Docs"
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
  - "RC1020"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC1020"
ms.assetid: 3e073ebf-9136-4bf8-ac6a-3c642ed64594
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable del compilador de recursos RC1020
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\#endif' inesperada  
  
 Una directiva `#endif` apareció sin una directiva `#if`, **\#ifdef** o **\#ifndef** coincidente.  
  
 Asegúrese de que hay una `#endif` coincidente para cada instrucción `#if`, **\#ifdef** y **\#ifndef.**