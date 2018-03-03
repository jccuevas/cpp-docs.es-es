---
title: Las herramientas del vinculador LNK1302 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1302
dev_langs:
- C++
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a5b9201608d6d457288c7ade9376147da08bcb9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1302"></a>Error de las herramientas del vinculador LNK1302
solamente se pueden vincular elementos .netmodule seguros; no se puede vincular el archivo .netmodule  
  
 Un archivo .netmodule (compilado con **/LN**) se pasó al vinculador en un intento del usuario de invocar la vinculación de MSIL.  Un módulo de C++ es válido para la vinculación de MSIL si se ha compilado con **/CLR: safe**.  
  
 Para corregir este error, compile con **/CLR: safe** para permitir la vinculación MSIL o pase el **/CLR** o **/CLR: pure** archivos obj al vinculador en lugar del módulo.  
  
 Para obtener más información, consulte  
  
-   [/LN (crear un módulo MSIL)](../../build/reference/ln-create-msil-module.md)  
  
-   [Archivos .netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md)