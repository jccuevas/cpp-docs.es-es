---
title: "Advertencia de las herramientas del vinculador LNK4086 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4086"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4086"
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia de las herramientas del vinculador LNK4086
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el punto de entrada 'función' no es \_\_stdcall con 12 bytes de argumentos; es posible que la imagen no se pueda ejecutar  
  
 El punto de entrada de una DLL debe ser `__stdcall`.  Vuelva a compilar la función con la opción [\/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md) o especifique `__stdcall` o WINAPI al definir la función.