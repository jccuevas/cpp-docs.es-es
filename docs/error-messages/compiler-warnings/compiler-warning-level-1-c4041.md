---
title: Compilador advertencia (nivel 1) C4041 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4041
dev_langs:
- C++
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfd8c933522e523329c41ebe666a5a7e3c198cb0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286102"
---
# <a name="compiler-warning-level-1-c4041"></a>Advertencia del compilador (nivel 1) C4041
límite del compilador : se va a finalizar el resultado del explorador  
  
 La información del explorador supera el límite del compilador.  
  
 Esta advertencia puede deberse a la compilación con [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (información del explorador con variables locales).  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Para corregir mediante las siguientes posibles soluciones  
  
1.  Compile con /Fr (información del explorador sin variables locales).  
  
2.  Deshabilite el resultado del explorador (compile sin /FR o /Fr).