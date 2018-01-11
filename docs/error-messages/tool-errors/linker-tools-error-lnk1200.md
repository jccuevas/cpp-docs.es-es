---
title: Las herramientas del vinculador LNK1200 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1200
dev_langs: C++
helpviewer_keywords: LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 70bf262d4f99c807e3488c1f9b2ed9e73b1eb715
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1200"></a>Error de las herramientas del vinculador LNK1200
Error al leer la base de datos de programa 'filename'  
  
 No se pudo leer la base de datos de programa (PDB).  
  
 Este error puede deberse a daños en el archivo.  
  
 Si `filename` es el archivo PDB de un archivo objeto, vuelva a compilar el archivo de objeto mediante [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
 Si `filename` es el archivo PDB para el archivo de salida principal y este error se produjo durante una vinculación incremental, elimine el archivo PDB y vuelva a vincular.