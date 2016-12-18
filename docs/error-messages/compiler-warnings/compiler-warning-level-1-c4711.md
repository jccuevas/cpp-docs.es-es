---
title: "Advertencia del compilador (nivel 1) C4711 | Microsoft Docs"
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
  - "C4711"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4711"
ms.assetid: 270506ab-fead-4328-b714-2978113be238
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4711
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

función 'función' seleccionada para expansión en línea  
  
 El compilador realizó la inclusión en línea en la función dada, si bien no estaba marcada como tal.  
  
 La advertencia C4711 está habilitada cuando se especifica [\/Ob2](../../build/reference/ob-inline-function-expansion.md).  
  
 La inclusión de funciones en línea tiene lugar a discreción del compilador.  Esta advertencia sólo tiene valor informativo.  
  
 De forma predeterminada, esta advertencia está desactivada.  Para habilitar una advertencia, utilice [\#pragma warning](../../preprocessor/warning.md).  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).