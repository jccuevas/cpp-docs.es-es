---
title: "Advertencia del compilador C4962 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4962"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4962"
ms.assetid: 62b156fe-04e5-4a6e-9339-6ab148185f87
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Advertencia del compilador C4962
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función': se han deshabilitado las optimizaciones guiadas por perfiles porque generaban datos de perfil incoherentes  
  
 Una función no se compiló con \/LTCG:PGO, porque los datos de la cuenta \(perfil\) para la función no son confiables. Es necesario volver a generar los perfiles para, a su vez, volver a crear el archivo .pgc que contiene los datos de perfil no confiables de esa función.  
  
 De forma predeterminada, esta advertencia está desactivada. Para obtener más información, consulte [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).