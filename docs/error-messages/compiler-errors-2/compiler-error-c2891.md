---
title: Error del compilador C2891 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2891
dev_langs: C++
helpviewer_keywords: C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6c35294472fe4142e7e6689adfc5f5f71c27b664
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2891"></a>Error del compilador C2891
'parámetro': no se puede adquirir la dirección de un parámetro de plantilla  
  
 No se puede adquirir la dirección de un parámetro de plantilla a menos que sea un valor l. Parámetros de tipo no son valores l porque no tienen ninguna dirección. También los valores sin tipo en listas de parámetros de plantilla que no son valores l no tiene una dirección. Este es un ejemplo de código que causa el Error del compilador C2891, porque el valor que se pasa como el parámetro de plantilla es una copia del argumento de plantilla generado por el compilador.  
  
```  
template <int i> int* f() { return &i; }  
```  
  
 Parámetros de plantilla que son valores l, como tipos de referencia, puede su dirección realizadas.  
  
```  
template <int& r> int* f() { return &r; }  
```  
  
 Para corregir este error, no tomar la dirección de un parámetro de plantilla a menos que sea un valor l.