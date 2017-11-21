---
title: Las herramientas del vinculador LNK1241 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1241
dev_langs: C++
helpviewer_keywords: LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3fee22549e7b5c831aa378dc5caffb9da69bff88
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1241"></a>Error de las herramientas del vinculador LNK1241
archivo de recursos 'archivo de recursos' ya se ha especificado  
  
 Este error se genera si ejecuta **cvtres** manualmente desde la línea de comandos y si, a continuación, pase el archivo .obj resultante de archivos al vinculador además a otros archivos. res.  
  
 Para especificar varios archivos. res, deben pasar todos al compilador como archivos .res, no desde los archivos .obj crean por **cvtres**.