---
title: Advertencia del compilador C4962 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4962
dev_langs: C++
helpviewer_keywords: C4962
ms.assetid: 62b156fe-04e5-4a6e-9339-6ab148185f87
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dae3bfa67f9f40072c8c200cd681b3babd92aff3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-c4962"></a>Advertencia del compilador C4962
'función': se han deshabilitado las optimizaciones guiadas por perfiles porque generaban datos de perfil incoherentes  
  
 Una función no se compiló con /LTCG:PGO, porque los datos de la cuenta (perfil) para la función no son confiables. Es necesario volver a generar los perfiles para, a su vez, volver a crear el archivo .pgc que contiene los datos de perfil no confiables de esa función.  
  
 De forma predeterminada, esta advertencia está desactivada. Para obtener más información, consulte [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).