---
title: Las herramientas del vinculador LNK1264 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1264
dev_langs: C++
helpviewer_keywords: LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d58bad22604509546e7f1645b56594653d33b070
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1264"></a>Error de las herramientas del vinculador LNK1264
/ LTCG: PGINSTRUMENT especificado, pero no requerida; de la generación de código Error de instrumentación  
  
 **/ LTCG: PGINSTRUMENT** especificó pero ningún archivo .obj se encontraron archivos que se compilaron con [/GL](../../build/reference/gl-whole-program-optimization.md). Instrumentación no puede tener lugar y el error en el vínculo. Debe haber al menos un archivo .obj en la línea de comandos que se compila con **/GL** para que pueda tener lugar la instrumentación.  
  
 Optimización guiada por perfiles (PGO) sólo está disponible en compiladores de 64 bits.