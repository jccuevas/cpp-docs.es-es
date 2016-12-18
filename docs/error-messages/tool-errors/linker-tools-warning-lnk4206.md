---
title: "Advertencia de las herramientas del vinculador LNK4206 | Microsoft Docs"
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
  - "LNK4206"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4206"
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de las herramientas del vinculador LNK4206
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se encontró información de tipo precompilado; no se vinculó 'nombredearchivo' o se ha reemplazado; se vinculará el objeto sin tener en cuenta información de depuración  
  
 El archivo objeto dado, compilado con [\/Yc](../../build/reference/yc-create-precompiled-header-file.md), no se especificó en el comando LINK o se sobrescribió.  
  
 Una situación habitual en la que se produce esta advertencia es cuando el archivo .obj que se compiló con \/Yc está en una biblioteca y ningún símbolo hace referencia a dicho archivo .obj desde el código.  En ese caso, el vinculador no utilizará \(o ni siquiera verá\) el archivo .obj.  En esta situación, debería volver a compilar el código y utilizar [\/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) para los objetos restantes \(los objetos que no se compilan con \/Yc\).